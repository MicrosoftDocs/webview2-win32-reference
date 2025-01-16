---
description: Receives the result of the `GetFavicon` method.
title: WebView2 Win32 C++ ICoreWebView2GetFaviconCompletedHandler
ms.date: 01/16/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetFaviconCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2GetFaviconCompletedHandler
- ICoreWebView2GetFaviconCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2GetFaviconCompletedHandler

```
interface ICoreWebView2GetFaviconCompletedHandler
  : public IUnknown
```

Receives the result of the `GetFavicon` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1293.44
WebView2 Win32 Prerelease |    1.0.1305

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, IStream * result)

