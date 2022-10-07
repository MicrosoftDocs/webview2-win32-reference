---
description: Receives the result of the `Print` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalPrintCompletedHandler
ms.date: 10/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalPrintCompletedHandler
---

# interface ICoreWebView2ExperimentalPrintCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalPrintCompletedHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, COREWEBVIEW2_PRINT_STATUS printStatus)

