---
description: Event args for the `DedicatedWorkerCreated` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs
- ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs.get_OriginalSourceFrameInfo
- ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs.get_Worker
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs
  : public IUnknown
```

Event args for the `DedicatedWorkerCreated` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_OriginalSourceFrameInfo](#get_originalsourceframeinfo) | The associated frame information that created the dedicated worker.
[get_Worker](#get_worker) | The dedicated worker that was created.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_OriginalSourceFrameInfo

The associated frame information that created the dedicated worker.

> public HRESULT [get_OriginalSourceFrameInfo](#get_originalsourceframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) ** value)

This can be used to get the frame source, name, frameId, and parent frame information.

#### get_Worker

The dedicated worker that was created.

> public HRESULT [get_Worker](#get_worker)([ICoreWebView2ExperimentalDedicatedWorker](icorewebview2experimentaldedicatedworker.md#icorewebview2experimentaldedicatedworker) ** value)

