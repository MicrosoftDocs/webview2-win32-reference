---
description: Receives the result of the `Remove` method.
title: WebView2 Win32 C++ ICoreWebView2BrowserExtensionRemoveCompletedHandler
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserExtensionRemoveCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2BrowserExtensionRemoveCompletedHandler
- ICoreWebView2BrowserExtensionRemoveCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BrowserExtensionRemoveCompletedHandler

```
interface ICoreWebView2BrowserExtensionRemoveCompletedHandler
  : public IUnknown
```

Receives the result of the `Remove` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

