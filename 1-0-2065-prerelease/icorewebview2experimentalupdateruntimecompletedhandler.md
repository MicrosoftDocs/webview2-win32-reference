---
description: The caller implements this interface to receive the UpdateRuntime result.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler
ms.date: 08/28/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler
- ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the UpdateRuntime result.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result for the UpdateRuntime operation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### Invoke

Provides the result for the UpdateRuntime operation.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, ICoreWebView2ExperimentalUpdateRuntimeResult * result)

`errorCode` will be S_OK if the update operation can be performed normally, regardless of whether we could update the Edge WebView2 Runtime. If an unexpected error interrupts the update operation, error code of that unexpected error would be set as `errorCode`. When update operation can be performed normally, but update resulted in failure, like download failed, the error code would be presented as `ExtendedError` property of ICoreWebView2ExperimentalUpdateRuntimeResult.

