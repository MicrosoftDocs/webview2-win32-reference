---
description: Event args for the `DedicatedWorkerCreated` event.
title: WebView2 Win32 C++ ICoreWebView2DedicatedWorkerCreatedEventArgs
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DedicatedWorkerCreatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2DedicatedWorkerCreatedEventArgs
- ICoreWebView2DedicatedWorkerCreatedEventArgs.get_OriginalSourceFrameInfo
- ICoreWebView2DedicatedWorkerCreatedEventArgs.get_Worker
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DedicatedWorkerCreatedEventArgs

```
interface ICoreWebView2DedicatedWorkerCreatedEventArgs
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
WebView2 Win32 Prerelease |    

## Members

#### get_OriginalSourceFrameInfo

The associated frame information that created the dedicated worker.

> public HRESULT [get_OriginalSourceFrameInfo](#get_originalsourceframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) ** value)

This can be used to get the frame source, name, frameId, and parent frame information.

#### get_Worker

The dedicated worker that was created.

> public HRESULT [get_Worker](#get_worker)([ICoreWebView2DedicatedWorker](icorewebview2dedicatedworker.md#icorewebview2dedicatedworker) ** value)

