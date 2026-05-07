---
description: Event args for the `ServiceWorkerRegistered` event.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerRegisteredEventArgs
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerRegisteredEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerRegisteredEventArgs
- ICoreWebView2ServiceWorkerRegisteredEventArgs.get_ServiceWorkerRegistration
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerRegisteredEventArgs

```
interface ICoreWebView2ServiceWorkerRegisteredEventArgs
  : public IUnknown
```

Event args for the `ServiceWorkerRegistered` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ServiceWorkerRegistration](#get_serviceworkerregistration) | The service worker that was registered.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_ServiceWorkerRegistration

The service worker that was registered.

> public HRESULT [get_ServiceWorkerRegistration](#get_serviceworkerregistration)([ICoreWebView2ServiceWorkerRegistration](icorewebview2serviceworkerregistration.md#icorewebview2serviceworkerregistration) ** value)

