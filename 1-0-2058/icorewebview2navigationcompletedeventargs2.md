---
description: 
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventArgs2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationCompletedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationCompletedEventArgs2
- ICoreWebView2NavigationCompletedEventArgs2.get_HttpStatusCode
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NavigationCompletedEventArgs2

```
interface ICoreWebView2NavigationCompletedEventArgs2
  : public ICoreWebView2NavigationCompletedEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HttpStatusCode](#get_httpstatuscode) | Gets the `HttpStatusCode` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_HttpStatusCode

Gets the `HttpStatusCode` property.

> public HRESULT [get_HttpStatusCode](#get_httpstatuscode)(INT32 * value)

