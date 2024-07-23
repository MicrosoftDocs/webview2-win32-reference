---
description: Receives the result of the `ClearCustomDataPartition` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler
ms.date: 07/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler
- ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler
  : public IUnknown
```

Receives the result of the `ClearCustomDataPartition` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

