---
description: Receives the result of the `PrintToPdfStream` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalPrintToPdfStreamCompletedHandler
ms.date: 10/04/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalPrintToPdfStreamCompletedHandler
---

# interface ICoreWebView2ExperimentalPrintToPdfStreamCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalPrintToPdfStreamCompletedHandler
  : public IUnknown
```

Receives the result of the `PrintToPdfStream` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

`errorCode` returns S_OK if the PrintToPdfStream operation succeeded. The printable pdf data is returned in the `pdfStream` object.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, IStream * pdfStream)

