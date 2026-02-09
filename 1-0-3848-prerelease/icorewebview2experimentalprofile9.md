---
description: This is an interface to control Enhanced Security Mode (ESM) level.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile9
ms.date: 02/09/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile9
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile9
- ICoreWebView2ExperimentalProfile9.get_EnhancedSecurityModeLevel
- ICoreWebView2ExperimentalProfile9.put_EnhancedSecurityModeLevel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile9

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile9
  : public IUnknown
```

This is an interface to control Enhanced Security Mode (ESM) level.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_EnhancedSecurityModeLevel](#get_enhancedsecuritymodelevel) | Gets the `EnhancedSecurityModeLevel` property.
[put_EnhancedSecurityModeLevel](#put_enhancedsecuritymodelevel) | The `EnhancedSecurityModeLevel` property allows you to control the Enhanced Security Mode level for WebView2 instances associated with a profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3796

## Members

#### get_EnhancedSecurityModeLevel

Gets the `EnhancedSecurityModeLevel` property.

> public HRESULT [get_EnhancedSecurityModeLevel](#get_enhancedsecuritymodelevel)(COREWEBVIEW2_ENHANCED_SECURITY_MODE_LEVEL * value)

#### put_EnhancedSecurityModeLevel

The `EnhancedSecurityModeLevel` property allows you to control the Enhanced Security Mode level for WebView2 instances associated with a profile.

> public HRESULT [put_EnhancedSecurityModeLevel](#put_enhancedsecuritymodelevel)(COREWEBVIEW2_ENHANCED_SECURITY_MODE_LEVEL value)

This level applies to the context of the profile. That is, all WebViews sharing the same profile are affected. The configuration is not persisted to the user data folder. The property is reset when the profile is recreated.

The default value is `COREWEBVIEW2_ENHANCED_SECURITY_MODE_LEVEL_OFF`.

When set to `Off`, Enhanced Security Mode is disabled. When set to `Strict`, the Enhanced Security Mode feature is enabled in Strict level.

See `COREWEBVIEW2_ENHANCED_SECURITY_MODE_LEVEL` for descriptions of levels.

Changes apply immediately to new navigation. Existing pages require a reload for the change to take effect.

```cpp
void SettingsComponent::SetEnhancedSecurityModeLevel(
    COREWEBVIEW2_ENHANCED_SECURITY_MODE_LEVEL value)
{
    wil::com_ptr<ICoreWebView2_13> webView2_13;
    webView2_13 = m_webView.try_query<ICoreWebView2_13>();

    if (webView2_13)
    {
        wil::com_ptr<ICoreWebView2Profile> profile;
        CHECK_FAILURE(webView2_13->get_Profile(&profile));

        auto experimentalProfile9 = profile.try_query<ICoreWebView2ExperimentalProfile9>();
        if (experimentalProfile9)
        {
            CHECK_FAILURE(experimentalProfile9->put_EnhancedSecurityModeLevel(value));

            const wchar_t* levelText = L"Off";
            if (value == COREWEBVIEW2_ENHANCED_SECURITY_MODE_LEVEL_STRICT)
            {
                levelText = L"Strict";
            }

            MessageBox(
                nullptr,
                (std::wstring(L"Enhanced Security Mode level is set to ") + levelText).c_str(),
                L"Enhanced Security Mode Level", MB_OK);
        }
    }
}
```

