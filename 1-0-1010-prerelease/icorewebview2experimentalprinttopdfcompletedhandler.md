---
description: Receives the result of the `PrintToPdf` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalPrintToPdfCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalPrintToPdfCompletedHandler
---

# interface ICoreWebView2ExperimentalPrintToPdfCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalPrintToPdfCompletedHandler
  : public IUnknown
```

Receives the result of the `PrintToPdf` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

If the print to PDF operation succeeds, `isSuccessful` is true. Otherwise, if the operation failed, `isSuccessful` is set to false. An invalid path returns `E_INVALIDARG`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, BOOL isSuccessful)

