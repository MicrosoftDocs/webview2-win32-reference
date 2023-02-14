---
description: Receives the result of the `Print` method.
title: WebView2 Win32 C++ ICoreWebView2PrintCompletedHandler
ms.date: 02/14/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintCompletedHandler
---

# interface ICoreWebView2PrintCompletedHandler

```
interface ICoreWebView2PrintCompletedHandler
  : public IUnknown
```

Receives the result of the `Print` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, COREWEBVIEW2_PRINT_STATUS printStatus)

