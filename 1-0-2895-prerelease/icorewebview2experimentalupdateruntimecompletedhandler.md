---
description: Receives the result of the `UpdateRuntime` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler
ms.date: 10/14/2024
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

Receives the result of the `UpdateRuntime` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalUpdateRuntimeResult](icorewebview2experimentalupdateruntimeresult.md#icorewebview2experimentalupdateruntimeresult) * result)

