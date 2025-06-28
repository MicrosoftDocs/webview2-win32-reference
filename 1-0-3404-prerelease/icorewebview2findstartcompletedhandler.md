---
description: Receives the result of the `Start` method.
title: WebView2 Win32 C++ ICoreWebView2FindStartCompletedHandler
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FindStartCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FindStartCompletedHandler
- ICoreWebView2FindStartCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FindStartCompletedHandler

```
interface ICoreWebView2FindStartCompletedHandler
  : public IUnknown
```

Receives the result of the `Start` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

