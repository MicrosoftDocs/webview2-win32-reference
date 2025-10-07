---
description: Receives the result of the `GetSharedWorkers` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler
- ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler
  : public IUnknown
```

Receives the result of the `GetSharedWorkers` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalSharedWorkerCollectionView](icorewebview2experimentalsharedworkercollectionview.md#icorewebview2experimentalsharedworkercollectionview) * result)

