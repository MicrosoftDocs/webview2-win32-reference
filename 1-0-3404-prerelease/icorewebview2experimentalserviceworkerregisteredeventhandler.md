---
description: Receives `ServiceWorkerRegistered` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler
- ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler
  : public IUnknown
```

Receives `ServiceWorkerRegistered` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalServiceWorkerManager](icorewebview2experimentalserviceworkermanager.md#icorewebview2experimentalserviceworkermanager) * sender, [ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs](icorewebview2experimentalserviceworkerregisteredeventargs.md#icorewebview2experimentalserviceworkerregisteredeventargs) * args)

