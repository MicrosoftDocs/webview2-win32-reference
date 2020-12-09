---
description: Receives the result of the `GetCookies` method.
title: WebView2 Win32 C++ ICoreWebView2GetCookiesCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/08/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetCookiesCompletedHandler
---

# interface ICoreWebView2GetCookiesCompletedHandler 

```
interface ICoreWebView2GetCookiesCompletedHandler
  : public IUnknown
```

Receives the result of the `GetCookies` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the completion status of the corresponding asynchronous method call.

The result is written to the cookie list provided in the `GetCookies` method call.

## Members

#### Invoke 

Provides the completion status of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT result, [ICoreWebView2CookieList](icorewebview2cookielist.md) * cookieList)

