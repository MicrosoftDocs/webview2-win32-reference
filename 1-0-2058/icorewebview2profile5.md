---
description: 
title: WebView2 Win32 C++ ICoreWebView2Profile5
ms.date: 09/08/2023
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

```
interface ICoreWebView2Profile5
  : public ICoreWebView2Profile4
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CookieManager](#get_cookiemanager) | Gets the `CookieManager` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_CookieManager

Gets the `CookieManager` property.

> public HRESULT [get_CookieManager](#get_cookiemanager)([ICoreWebView2CookieManager](icorewebview2cookiemanager.md) ** value)

