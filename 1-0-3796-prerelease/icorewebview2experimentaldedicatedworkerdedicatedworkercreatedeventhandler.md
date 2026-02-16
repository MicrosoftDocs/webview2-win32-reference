---
description: Receives `DedicatedWorkerCreated` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler
- ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler
  : public IUnknown
```

Receives `DedicatedWorkerCreated` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalDedicatedWorker](icorewebview2experimentaldedicatedworker.md#icorewebview2experimentaldedicatedworker) * sender, [ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs](icorewebview2experimentaldedicatedworkercreatedeventargs.md#icorewebview2experimentaldedicatedworkercreatedeventargs) * args)

