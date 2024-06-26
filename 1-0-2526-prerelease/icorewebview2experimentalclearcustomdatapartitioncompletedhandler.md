---
description: The caller implements this interface to receive the ClearCustomDataPartition result.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler
ms.date: 06/19/2024
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClearCustomDataPartitionCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the ClearCustomDataPartition result.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provide the completion status of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### Invoke

Provide the completion status of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

