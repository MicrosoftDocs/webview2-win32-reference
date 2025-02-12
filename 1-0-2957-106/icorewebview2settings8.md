---
description: A continuation of the ICoreWebView2Settings interface to manage smartscreen.
title: WebView2 Win32 C++ ICoreWebView2Settings8
ms.date: 01/13/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings8
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings8
- ICoreWebView2Settings8.get_IsReputationCheckingRequired
- ICoreWebView2Settings8.put_IsReputationCheckingRequired
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings8

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Settings8
  : public ICoreWebView2Settings7
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface to manage smartscreen.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsReputationCheckingRequired](#get_isreputationcheckingrequired) | Gets the `IsReputationCheckingRequired` property.
[put_IsReputationCheckingRequired](#put_isreputationcheckingrequired) | SmartScreen helps webviews identify reported phishing and malware websites and also helps users make informed decisions about downloads.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1722.45
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_IsReputationCheckingRequired

Gets the `IsReputationCheckingRequired` property.

> public HRESULT [get_IsReputationCheckingRequired](#get_isreputationcheckingrequired)(BOOL * value)

#### put_IsReputationCheckingRequired

SmartScreen helps webviews identify reported phishing and malware websites and also helps users make informed decisions about downloads.

> public HRESULT [put_IsReputationCheckingRequired](#put_isreputationcheckingrequired)(BOOL value)

`IsReputationCheckingRequired` is used to control whether SmartScreen enabled or not. SmartScreen is enabled or disabled for all CoreWebView2s using the same user data folder. If CoreWebView2Setting.IsReputationCheckingRequired is true for any CoreWebView2 using the same user data folder, then SmartScreen is enabled. If CoreWebView2Setting.IsReputationCheckingRequired is false for all CoreWebView2 using the same user data folder, then SmartScreen is disabled. When it is changed, the change will be applied to all WebViews using the same user data folder on the next navigation or download. The default value for `IsReputationCheckingRequired` is true. If the newly created CoreWebview2 does not set SmartScreen to false, when navigating(Such as Navigate(), LoadDataUrl(), ExecuteScript(), etc.), the default value will be applied to all CoreWebview2 using the same user data folder. SmartScreen of WebView2 apps can be controlled by Windows system setting "SmartScreen for Microsoft Edge", specially, for WebView2 in Windows Store apps, SmartScreen is controlled by another Windows system setting "SmartScreen for Microsoft Store apps". When the Windows setting is enabled, the SmartScreen operates under the control of the `IsReputationCheckingRequired`. When the Windows setting is disabled, the SmartScreen will be disabled regardless of the `IsReputationCheckingRequired` value set in WebView2 apps. In other words, under this circumstance the value of `IsReputationCheckingRequired` will be saved but overridden by system setting. Upon re-enabling the Windows setting, the CoreWebview2 will reference the `IsReputationCheckingRequired` to determine the SmartScreen status. 
```cpp
            CHECK_FEATURE_RETURN(m_settings8);

            BOOL is_smart_screen_enabled;
            CHECK_FAILURE(
                m_settings8->get_IsReputationCheckingRequired(&is_smart_screen_enabled));
            if (is_smart_screen_enabled)
            {
                CHECK_FAILURE(m_settings8->put_IsReputationCheckingRequired(false));
                MessageBox(
                    nullptr, L"SmartScreen is disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings8->put_IsReputationCheckingRequired(true));
                MessageBox(
                    nullptr, L"SmartScreen is enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

