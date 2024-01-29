---
description: The caller implements this method to receive the result of the GetCookies method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetCookiesCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetCookiesCompletedHandler
---

# interface ICoreWebView2ExperimentalGetCookiesCompletedHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetCookiesCompletedHandler
  : public IUnknown
```

The caller implements this method to receive the result of the GetCookies method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status of the corresponding asynchronous method call.

The result is written to the cookie list provided in the GetCookies method call.

## Members

#### Invoke 

Called to provide the implementer with the completion status of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT result, [ICoreWebView2ExperimentalCookieList](icorewebview2experimentalcookielist.md) * cookieList)

