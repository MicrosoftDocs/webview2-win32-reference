---
description: Receives `Destroying` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler
ms.date: 07/08/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler
- ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler
  : public IUnknown
```

Receives `Destroying` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalSharedWorker](icorewebview2experimentalsharedworker.md#icorewebview2experimentalsharedworker) * sender, IUnknown * args)

