---
description: Event args for the `SharedWorkerCreated` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs
- ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs.get_Worker
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs
  : public IUnknown
```

Event args for the `SharedWorkerCreated` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Worker](#get_worker) | The shared worker that was created.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Worker

The shared worker that was created.

> public HRESULT [get_Worker](#get_worker)([ICoreWebView2ExperimentalSharedWorker](icorewebview2experimentalsharedworker.md#icorewebview2experimentalsharedworker) ** value)

