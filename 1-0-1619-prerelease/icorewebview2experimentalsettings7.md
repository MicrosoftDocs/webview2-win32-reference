---
description: A continuation of the ICoreWebView2Settings interface to manage smartscreen.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings7
ms.date: 01/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings7
---

# interface ICoreWebView2ExperimentalSettings7

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings7
  : public IUnknown
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md) interface to manage smartscreen.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsReputationCheckingRequired](#get_isreputationcheckingrequired) | SmartScreen helps webviews identify reported phishing and malware websites and also helps users make informed decisions about downloads.
[put_IsReputationCheckingRequired](#put_isreputationcheckingrequired) | Sets whether this webview2 instance needs SmartScreen protection for its content.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1414

## Members

#### get_IsReputationCheckingRequired

SmartScreen helps webviews identify reported phishing and malware websites and also helps users make informed decisions about downloads.

> public HRESULT [get_IsReputationCheckingRequired](#get_isreputationcheckingrequired)(BOOL * value)

`IsReputationCheckingRequired` is used to control whether SmartScreen enabled or not. SmartScreen is enabled or disabled for all CoreWebView2s using the same user data folder. If CoreWebView2Setting.IsReputationCheckingRequired is true for any CoreWebView2 using the same user data folder, then SmartScreen is enabled. If CoreWebView2Setting.IsReputationCheckingRequired is false for all CoreWebView2 using the same user data folder, then SmartScreen is disabled. When it is changed, the change will be applied to all WebViews using the same user data folder on the next navigation or download. The default value for `IsReputationCheckingRequired` is true. If the newly created CoreWebview2 does not set SmartScreen to false, when navigating(Such as Navigate(), LoadDataUrl(), ExecuteScript(), etc.), the default value will be applied to all CoreWebview2 using the same user data folder. 
```cpp
            wil::com_ptr<ICoreWebView2ExperimentalSettings7> experimentalSettings;
            experimentalSettings = m_settings.try_query<ICoreWebView2ExperimentalSettings7>();
            CHECK_FEATURE_RETURN(experimentalSettings);

            BOOL is_smart_screen_enabled;
            CHECK_FAILURE(experimentalSettings->get_IsReputationCheckingRequired(
                &is_smart_screen_enabled));
            if (is_smart_screen_enabled)
            {
                CHECK_FAILURE(experimentalSettings->put_IsReputationCheckingRequired(false));
                MessageBox(
                    nullptr, L"SmartScreen is disable after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(experimentalSettings->put_IsReputationCheckingRequired(true));
                MessageBox(
                    nullptr, L"SmartScreen is enable after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsReputationCheckingRequired

Sets whether this webview2 instance needs SmartScreen protection for its content.

> public HRESULT [put_IsReputationCheckingRequired](#put_isreputationcheckingrequired)(BOOL value)

Set the `IsReputationCheckingRequired` property.

