---
description: Event args for the `ServiceWorkerRegistered` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs
- ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs.get_ServiceWorkerRegistration
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs
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
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_ServiceWorkerRegistration

The service worker that was registered.

> public HRESULT [get_ServiceWorkerRegistration](#get_serviceworkerregistration)([ICoreWebView2ExperimentalServiceWorkerRegistration](icorewebview2experimentalserviceworkerregistration.md#icorewebview2experimentalserviceworkerregistration) ** value)

