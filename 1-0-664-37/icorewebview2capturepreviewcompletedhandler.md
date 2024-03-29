---
description: The caller implements this method to receive the result of the CapturePreview method.
title: WebView2 Win32 C++ ICoreWebView2CapturePreviewCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/29/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CapturePreviewCompletedHandler
---

# interface ICoreWebView2CapturePreviewCompletedHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CapturePreviewCompletedHandler
  : public IUnknown
```

The caller implements this method to receive the result of the CapturePreview method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status of the corresponding asynchronous method call.

The result is written to the stream provided in the CapturePreview method call.

## Members

#### Invoke 

Called to provide the implementer with the completion status of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

