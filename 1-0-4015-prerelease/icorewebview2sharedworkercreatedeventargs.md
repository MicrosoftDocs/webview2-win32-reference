---
description: Event args for the `SharedWorkerCreated` event.
title: WebView2 Win32 C++ ICoreWebView2SharedWorkerCreatedEventArgs
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SharedWorkerCreatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2SharedWorkerCreatedEventArgs
- ICoreWebView2SharedWorkerCreatedEventArgs.get_Worker
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SharedWorkerCreatedEventArgs

```
interface ICoreWebView2SharedWorkerCreatedEventArgs
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

> public HRESULT [get_Worker](#get_worker)([ICoreWebView2SharedWorker](icorewebview2sharedworker.md#icorewebview2sharedworker) ** value)

