---
description: Receives `Unregistering` events.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerRegistrationUnregisteringEventHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerRegistrationUnregisteringEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerRegistrationUnregisteringEventHandler
- ICoreWebView2ServiceWorkerRegistrationUnregisteringEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerRegistrationUnregisteringEventHandler

```
interface ICoreWebView2ServiceWorkerRegistrationUnregisteringEventHandler
  : public IUnknown
```

Receives `Unregistering` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ServiceWorkerRegistration](icorewebview2serviceworkerregistration.md#icorewebview2serviceworkerregistration) * sender, IUnknown * args)

