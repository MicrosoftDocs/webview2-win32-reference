---
description: Receives the result of the `CapturePreview` method.
title: WebView2 Win32 C++ ICoreWebView2CapturePreviewCompletedHandler
ms.date: 07/31/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CapturePreviewCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2CapturePreviewCompletedHandler
- ICoreWebView2CapturePreviewCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CapturePreviewCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CapturePreviewCompletedHandler
  : public IUnknown
```

Receives the result of the `CapturePreview` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the completion status of the corresponding asynchronous method.

The result is written to the stream provided in the `CapturePreview` method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the completion status of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

