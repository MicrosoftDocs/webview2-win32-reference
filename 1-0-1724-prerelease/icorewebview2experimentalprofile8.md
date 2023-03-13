---
description: This is the ICoreWebView2 experimental interface for cookie manager.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile8
ms.date: 03/13/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile8
---

# interface ICoreWebView2ExperimentalProfile8

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile8
  : public IUnknown
```

This is the [ICoreWebView2](icorewebview2.md) experimental interface for cookie manager.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CookieManager](#get_cookiemanager) | Get the cookie manager for the profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_CookieManager

Get the cookie manager for the profile.

> public HRESULT [get_CookieManager](#get_cookiemanager)([ICoreWebView2CookieManager](icorewebview2cookiemanager.md) ** cookieManager)

All CoreWebView2s associated with this profile share the same cookie values. Changes to cookies in this cookie manager apply to all CoreWebView2s associated with this profile. See [ICoreWebView2CookieManager](icorewebview2cookiemanager.md).

```cpp
        auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
        CHECK_FEATURE_RETURN_EMPTY(webView2_13);
        wil::com_ptr<ICoreWebView2Profile> webView2Profile;
        CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
        auto webView2ExperimentalProfile8 =
            webView2Profile.try_query<ICoreWebView2ExperimentalProfile8>();
        CHECK_FEATURE_RETURN_EMPTY(webView2ExperimentalProfile8);
        CHECK_FAILURE(webView2ExperimentalProfile8->get_CookieManager(&m_cookieManager));
```

