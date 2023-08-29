---
description: This is the ICoreWebView2Profile interface for cookie manager.
title: WebView2 Win32 C++ ICoreWebView2Profile5
ms.date: 08/30/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile5
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile5
- ICoreWebView2Profile5.get_CookieManager
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile5

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Profile5
  : public ICoreWebView2Profile4
```

This is the [ICoreWebView2Profile](icorewebview2profile.md) interface for cookie manager.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CookieManager](#get_cookiemanager) | Get the cookie manager for the profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

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
        auto webView2Profile5 = webView2Profile.try_query<ICoreWebView2Profile5>();
        CHECK_FEATURE_RETURN_EMPTY(webView2Profile5);
        CHECK_FAILURE(webView2Profile5->get_CookieManager(&m_cookieManager));
```

