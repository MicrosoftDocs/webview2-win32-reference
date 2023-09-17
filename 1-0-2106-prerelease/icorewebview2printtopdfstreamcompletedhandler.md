---
description: Receives the result of the `PrintToPdfStream` method.
title: WebView2 Win32 C++ ICoreWebView2PrintToPdfStreamCompletedHandler
ms.date: 09/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintToPdfStreamCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2PrintToPdfStreamCompletedHandler
- ICoreWebView2PrintToPdfStreamCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PrintToPdfStreamCompletedHandler

```
interface ICoreWebView2PrintToPdfStreamCompletedHandler
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
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, IStream * pdfStream)

