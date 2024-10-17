---
description: This is the ICoreWebView2Profile interface for the permission management APIs.
title: WebView2 Win32 C++ ICoreWebView2Profile4
ms.date: 08/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile4
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile4
- ICoreWebView2Profile4.GetNonDefaultPermissionSettings
- ICoreWebView2Profile4.SetPermissionState
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile4

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Profile4
  : public ICoreWebView2Profile3
```

This is the [ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) interface for the permission management APIs.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetNonDefaultPermissionSettings](#getnondefaultpermissionsettings) | Invokes the handler with a collection of all nondefault permission settings.
[SetPermissionState](#setpermissionstate) | Sets permission state for the given permission kind and origin asynchronously.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### GetNonDefaultPermissionSettings

Invokes the handler with a collection of all nondefault permission settings.

> public HRESULT [GetNonDefaultPermissionSettings](#getnondefaultpermissionsettings)([ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler](icorewebview2getnondefaultpermissionsettingscompletedhandler.md#icorewebview2getnondefaultpermissionsettingscompletedhandler) * handler)

Use this method to get the permission state set in the current and previous sessions.

```cpp
    CHECK_FAILURE(webView2_13->add_DOMContentLoaded(
        Callback<ICoreWebView2DOMContentLoadedEventHandler>(
            [this](
                ICoreWebView2* sender, ICoreWebView2DOMContentLoadedEventArgs* args) -> HRESULT
            {
                wil::unique_cotaskmem_string source;
                CHECK_FAILURE(sender->get_Source(&source));
                // Permission management APIs are only used on the app's
                // permission management page.
                if (source.get() != m_sampleUri)
                {
                    return S_OK;
                }
                // Get all the nondefault permissions and post them to the
                // app's permission management page. The permission management
                // page can present a list of custom permissions set for this
                // profile and let the end user modify them.
                CHECK_FAILURE(m_webViewProfile4->GetNonDefaultPermissionSettings(
                    Callback<ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler>(
                        [this, sender](
                            HRESULT code,
                            ICoreWebView2PermissionSettingCollectionView* collectionView)
                            -> HRESULT
                        {
                            UINT32 count;
                            collectionView->get_Count(&count);
                            for (UINT32 i = 0; i < count; i++)
                            {
                                wil::com_ptr<ICoreWebView2PermissionSetting> setting;
                                CHECK_FAILURE(collectionView->GetValueAtIndex(i, &setting));
                                COREWEBVIEW2_PERMISSION_KIND kind;
                                CHECK_FAILURE(setting->get_PermissionKind(&kind));
                                std::wstring kind_string = PermissionKindToString(kind);
                                COREWEBVIEW2_PERMISSION_STATE state;
                                CHECK_FAILURE(setting->get_PermissionState(&state));
                                wil::unique_cotaskmem_string origin;
                                CHECK_FAILURE(setting->get_PermissionOrigin(&origin));
                                std::wstring state_string = PermissionStateToString(state);
                                std::wstring reply = L"{\"PermissionSetting\": \"" +
                                                     kind_string + L", " + origin.get() +
                                                     L", " + state_string + L"\"}";
                                CHECK_FAILURE(sender->PostWebMessageAsJson(reply.c_str()));
                            }
                            return S_OK;
                        })
                        .Get()));
                return S_OK;
            })
            .Get(),
        &m_DOMContentLoadedToken));
```

#### SetPermissionState

Sets permission state for the given permission kind and origin asynchronously.

> public HRESULT [SetPermissionState](#setpermissionstate)(COREWEBVIEW2_PERMISSION_KIND PermissionKind, LPCWSTR origin, COREWEBVIEW2_PERMISSION_STATE State, [ICoreWebView2SetPermissionStateCompletedHandler](icorewebview2setpermissionstatecompletedhandler.md#icorewebview2setpermissionstatecompletedhandler) * handler)

The change persists across sessions until it is changed by another call to `SetPermissionState`, or by setting the `State` property in `PermissionRequestedEventArgs`. Setting the state to `COREWEBVIEW2_PERMISSION_STATE_DEFAULT` will erase any state saved in the profile and restore the default behavior. The origin should have a valid scheme and host (e.g. "https://www.example.com"), otherwise the method fails with `E_INVALIDARG`. Additional URI parts like path and fragment are ignored. For example, "https://wwww.example.com/app1/index.html/" is treated the same as "https://wwww.example.com". See the [MDN origin definition](https://developer.mozilla.org/docs/Glossary/Origin) for more details.

```cpp
// The app's permission management page can provide a way for the end user to
// change permissions. For example, a button on the page can trigger a dialog,
// where the user specifies the desired permission kind, origin, and state.
void ScenarioPermissionManagement::ShowSetPermissionDialog()
{
    PermissionDialog dialog(m_appWindow->GetMainWindow(), permissionKinds, permissionStates);
    if (dialog.confirmed && m_webViewProfile4)
    {
        // Example: m_webViewProfile4->SetPermissionState(
        //    COREWEBVIEW2_PERMISSION_KIND_GEOLOCATION,
        //    L"https://example.com",
        //    COREWEBVIEW2_PERMISSION_STATE_DENY
        //    SetPermissionStateCallback);
        CHECK_FAILURE(m_webViewProfile4->SetPermissionState(
            dialog.kind, dialog.origin.c_str(), dialog.state,
            Callback<ICoreWebView2SetPermissionStateCompletedHandler>(
                [this](HRESULT error) -> HRESULT
                {
                    m_webView->Reload();
                    return S_OK;
                })
                .Get()));
    }
}
```

