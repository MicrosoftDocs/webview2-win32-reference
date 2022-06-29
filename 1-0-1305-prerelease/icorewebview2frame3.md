---
description: This is an extension of the ICoreWebView2Frame interface that supports PermissionRequested.
title: WebView2 Win32 C++ ICoreWebView2Frame3
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame3
---

# interface ICoreWebView2Frame3

```
interface ICoreWebView2Frame3
  : public ICoreWebView2Frame2
```

This is an extension of the ICoreWebView2Frame interface that supports PermissionRequested.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_PermissionRequested](#add_permissionrequested) | Add an event handler for the `PermissionRequested` event.
[remove_PermissionRequested](#remove_permissionrequested) | Remove an event handler previously added with `add_PermissionRequested`

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### add_PermissionRequested

Add an event handler for the `PermissionRequested` event.

> public HRESULT [add_PermissionRequested](#add_permissionrequested)([ICoreWebView2FramePermissionRequestedEventHandler](icorewebview2framepermissionrequestedeventhandler.md) * handler, EventRegistrationToken * token)

`PermissionRequested` is raised when content in an iframe any of its descendant iframes requests permission to privileged resources.

This relates to the `PermissionRequested` event on the `CoreWebView2`. Both these events will be raised in the case of an iframe requesting permission. The `CoreWebView2Frame`'s event handlers will be invoked before the event handlers on the `CoreWebView2`. If the `Handled` property of the `PermissionRequestedEventArgs` is set to TRUE within the `CoreWebView2Frame` event handler, then the event will not be raised on the `CoreWebView2`, and it's event handlers will not be invoked.

In the case of nested iframes, the 'PermissionRequested' event will be raised from the top level iframe.

If a deferral is not taken on the event args, the subsequent scripts are blocked until the event handler returns. If a deferral is taken, the scripts are blocked until the deferral is completed.

```cpp
    m_webView4 = m_webView.try_query<ICoreWebView2_4>();
    if (m_webView4)
    {
        CHECK_FAILURE(m_webView4->add_FrameCreated(
            Callback<ICoreWebView2FrameCreatedEventHandler>(
                [this](ICoreWebView2* sender, ICoreWebView2FrameCreatedEventArgs* args) -> HRESULT {
                    wil::com_ptr<ICoreWebView2Frame> webviewFrame;
                    CHECK_FAILURE(args->get_Frame(&webviewFrame));

                    m_frame3 = webviewFrame.try_query<ICoreWebView2Frame3>();
                    if (m_frame3)
                    {
                        CHECK_FAILURE(m_frame3->add_PermissionRequested(
                            Callback<ICoreWebView2FramePermissionRequestedEventHandler>(
                                this, &ScenarioIFrameDevicePermission::OnPermissionRequested
                            ).Get(),
                            &m_PermissionRequestedToken));
                    }
                    else {
                        m_appWindow->RunAsync([]{ FeatureNotAvailable(); });
                    }
                    m_webView4->remove_FrameCreated(m_FrameCreatedToken);
                    return S_OK;
            }).Get(),
            &m_FrameCreatedToken));
    }
    else
    {
        FeatureNotAvailable();
    }
```

```cpp
HRESULT ScenarioIFrameDevicePermission::OnPermissionRequested(
    ICoreWebView2Frame* sender, ICoreWebView2PermissionRequestedEventArgs2* args)
{
    // If we set Handled to true, then we will not fire the PermissionRequested
    // event off of the CoreWebView2.
    args->put_Handled(true);

    // Obtain a deferral for the event so that the CoreWebView2
    // doesn't examine the properties we set on the event args until
    // after we call the Complete method asynchronously later.
    wil::com_ptr<ICoreWebView2Deferral> deferral;
    CHECK_FAILURE(args->GetDeferral(&deferral));

    // Do the rest asynchronously, to avoid calling MessageBox in an event handler.
    m_appWindow->RunAsync([this, deferral, args]
    {
        COREWEBVIEW2_PERMISSION_KIND kind = COREWEBVIEW2_PERMISSION_KIND_UNKNOWN_PERMISSION;
        BOOL userInitiated = FALSE;
        wil::unique_cotaskmem_string uri;
        CHECK_FAILURE(args->get_PermissionKind(&kind));
        CHECK_FAILURE(args->get_IsUserInitiated(&userInitiated));
        CHECK_FAILURE(args->get_Uri(&uri));

        COREWEBVIEW2_PERMISSION_STATE state;

        auto cached_key = std::make_tuple(std::wstring(uri.get()), kind, userInitiated);
        auto cached_permission = m_cached_permissions.find(cached_key);
        if (cached_permission != m_cached_permissions.end())
        {
            state = (cached_permission->second
                ? COREWEBVIEW2_PERMISSION_STATE_ALLOW
                : COREWEBVIEW2_PERMISSION_STATE_DENY);
        }
        else
        {
            std::wstring message = L"An iframe has requested device permission for ";
            message += SettingsComponent::NameOfPermissionKind(kind);
            message += L" to the website at ";
            message += uri.get();
            message += L"?\n\n";
            message += L"Do you want to grant permission?\n";
            message += (userInitiated
                ? L"This request came from a user gesture."
                : L"This request did not come from a user gesture.");

            int response = MessageBox(
                nullptr, message.c_str(), L"Permission Request",
                MB_YESNOCANCEL | MB_ICONWARNING);
            switch (response) {
                case IDYES:
                    m_cached_permissions[cached_key] = true;
                    state = COREWEBVIEW2_PERMISSION_STATE_ALLOW;
                    break;
                case IDNO:
                    m_cached_permissions[cached_key] = false;
                    state = COREWEBVIEW2_PERMISSION_STATE_DENY;
                    break;
                default:
                    state = COREWEBVIEW2_PERMISSION_STATE_DEFAULT;
                    break;
            }
        }

        CHECK_FAILURE(args->put_State(state));
        CHECK_FAILURE(deferral->Complete());
    });
    return S_OK;
}
```

#### remove_PermissionRequested

Remove an event handler previously added with `add_PermissionRequested`

> public HRESULT [remove_PermissionRequested](#remove_permissionrequested)(EventRegistrationToken token)

