---
description: This is an interface to control Enhanced Security Mode (ESM) state.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile17
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile17
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile17
- ICoreWebView2ExperimentalProfile17.get_EnhancedSecurityModeState
- ICoreWebView2ExperimentalProfile17.put_EnhancedSecurityModeState
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile17

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile17
  : public IUnknown
```

This is an interface to control Enhanced Security Mode (ESM) state.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_EnhancedSecurityModeState](#get_enhancedsecuritymodestate) | Gets the `EnhancedSecurityModeState` property.
[put_EnhancedSecurityModeState](#put_enhancedsecuritymodestate) | The `EnhancedSecurityModeState` property allows you to control whether Enhanced Security Mode is enabled or disabled for WebView2 instances associated with a profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_EnhancedSecurityModeState

Gets the `EnhancedSecurityModeState` property.

> public HRESULT [get_EnhancedSecurityModeState](#get_enhancedsecuritymodestate)(COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE * value)

#### put_EnhancedSecurityModeState

The `EnhancedSecurityModeState` property allows you to control whether Enhanced Security Mode is enabled or disabled for WebView2 instances associated with a profile.

> public HRESULT [put_EnhancedSecurityModeState](#put_enhancedsecuritymodestate)(COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE value)

This applies to all WebViews sharing the same profile. The configuration is not persisted to the user data folder. The property is reset when the profile is recreated.

The default value is `COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE_DISABLED`.

When set to `Disabled`, Enhanced Security Mode is disabled. When set to `Enabled`, Enhanced Security Mode is enabled.

See `COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE` for descriptions of states.

Changes apply immediately to new navigation. Existing pages require a reload for the change to take effect.

```cpp
void SettingsComponent::SetEnhancedSecurityModeState(
    COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE value)
{
    wil::com_ptr<ICoreWebView2_13> webView2_13;
    webView2_13 = m_webView.try_query<ICoreWebView2_13>();

    if (webView2_13)
    {
        wil::com_ptr<ICoreWebView2Profile> profile;
        CHECK_FAILURE(webView2_13->get_Profile(&profile));

        auto experimentalProfile17 = profile.try_query<ICoreWebView2ExperimentalProfile17>();
        if (experimentalProfile17)
        {
            CHECK_FAILURE(experimentalProfile17->put_EnhancedSecurityModeState(value));

            const wchar_t* stateText = L"Disabled";
            if (value == COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE_ENABLED)
            {
                stateText = L"Enabled";
            }

            MessageBox(
                nullptr,
                (std::wstring(L"Enhanced Security Mode state is set to ") + stateText).c_str(),
                L"Enhanced Security Mode State", MB_OK);
        }
    }
}
```

