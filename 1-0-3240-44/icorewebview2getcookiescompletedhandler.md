---
description: Receives the result of the `GetCookies` method.
title: WebView2 Win32 C++ ICoreWebView2GetCookiesCompletedHandler
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetCookiesCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2GetCookiesCompletedHandler
- ICoreWebView2GetCookiesCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2GetCookiesCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2GetCookiesCompletedHandler
  : public IUnknown
```

Receives the result of the `GetCookies` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2CookieList](icorewebview2cookielist.md#icorewebview2cookielist) * result)

