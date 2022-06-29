---
description: This interface is an extension of ICoreWebView2_12 that supports Profile API.
title: WebView2 Win32 C++ ICoreWebView2_13
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_13
---

# interface ICoreWebView2_13

```
interface ICoreWebView2_13
  : public ICoreWebView2_12
```

This interface is an extension of ICoreWebView2_12 that supports Profile API.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Profile](#get_profile) | The associated [ICoreWebView2Profile](icorewebview2profile.md) object.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1210.39
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_Profile

The associated ICoreWebView2Profile object.

> public HRESULT [get_Profile](#get_profile)([ICoreWebView2Profile](icorewebview2profile.md) ** value)

If this CoreWebView2 was created with a CoreWebView2ControllerOptions, the CoreWebView2Profile will match those specified options. Otherwise if this CoreWebView2 was created without a CoreWebView2ControllerOptions, then this will be the default CoreWebView2Profile for the corresponding CoreWebView2Environment.

```cpp
        auto webView2_13 = coreWebView2.try_query<ICoreWebView2_13>();
        if (webView2_13)
        {
            wil::com_ptr<ICoreWebView2Profile> profile;
            CHECK_FAILURE(webView2_13->get_Profile(&profile));
            wil::unique_cotaskmem_string profile_name;
            CHECK_FAILURE(profile->get_ProfileName(&profile_name));
            m_profileName = profile_name.get();
            BOOL inPrivate = FALSE;
            CHECK_FAILURE(profile->get_IsInPrivateModeEnabled(&inPrivate));
            if (!m_webviewOption.downloadPath.empty())
            {
                CHECK_FAILURE(profile->put_DefaultDownloadFolderPath(
                    m_webviewOption.downloadPath.c_str()));
            }

            // update window title with m_profileName
            UpdateAppTitle();

            // update window icon
            SetAppIcon(inPrivate);
        }
```

