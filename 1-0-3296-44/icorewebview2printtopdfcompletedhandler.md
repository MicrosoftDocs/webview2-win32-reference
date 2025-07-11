---
description: Receives the result of the `PrintToPdf` method.
title: WebView2 Win32 C++ ICoreWebView2PrintToPdfCompletedHandler
ms.date: 05/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintToPdfCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2PrintToPdfCompletedHandler
- ICoreWebView2PrintToPdfCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PrintToPdfCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2PrintToPdfCompletedHandler
  : public IUnknown
```

Receives the result of the `PrintToPdf` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1020.30
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, BOOL result)

