---
description: Receives `Destroying` events.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerDestroyingEventHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerDestroyingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerDestroyingEventHandler
- ICoreWebView2ServiceWorkerDestroyingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerDestroyingEventHandler

```
interface ICoreWebView2ServiceWorkerDestroyingEventHandler
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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ServiceWorker](icorewebview2serviceworker.md#icorewebview2serviceworker) * sender, IUnknown * args)

