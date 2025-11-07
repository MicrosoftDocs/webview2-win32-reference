---
description: Event args for the `ServiceWorkerActivated` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs
- ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs.get_ActiveServiceWorker
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs
  : public IUnknown
```

Event args for the `ServiceWorkerActivated` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ActiveServiceWorker](#get_activeserviceworker) | The service worker that was activated.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_ActiveServiceWorker

The service worker that was activated.

> public HRESULT [get_ActiveServiceWorker](#get_activeserviceworker)([ICoreWebView2ExperimentalServiceWorker](icorewebview2experimentalserviceworker.md#icorewebview2experimentalserviceworker) ** value)

