---
description: Receives `Destroying` events.
title: WebView2 Win32 C++ ICoreWebView2SharedWorkerDestroyingEventHandler
ms.date: 06/30/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SharedWorkerDestroyingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2SharedWorkerDestroyingEventHandler
- ICoreWebView2SharedWorkerDestroyingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SharedWorkerDestroyingEventHandler

```
interface ICoreWebView2SharedWorkerDestroyingEventHandler
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
WebView2 Win32            |    1.0.4022.49
WebView2 Win32 Prerelease |    1.0.4015

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2SharedWorker](icorewebview2sharedworker.md#icorewebview2sharedworker) * sender, IUnknown * args)

