---
description: Receives `ServiceWorkerRegistered` events.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerRegisteredEventHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerRegisteredEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerRegisteredEventHandler
- ICoreWebView2ServiceWorkerRegisteredEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerRegisteredEventHandler

```
interface ICoreWebView2ServiceWorkerRegisteredEventHandler
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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ServiceWorkerManager](icorewebview2serviceworkermanager.md#icorewebview2serviceworkermanager) * sender, [ICoreWebView2ServiceWorkerRegisteredEventArgs](icorewebview2serviceworkerregisteredeventargs.md#icorewebview2serviceworkerregisteredeventargs) * args)

