---
description: Event args for the `ServiceWorkerActivated` event.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerActivatedEventArgs
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerActivatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerActivatedEventArgs
- ICoreWebView2ServiceWorkerActivatedEventArgs.get_ActiveServiceWorker
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerActivatedEventArgs

```
interface ICoreWebView2ServiceWorkerActivatedEventArgs
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
WebView2 Win32 Prerelease |    

## Members

#### get_ActiveServiceWorker

The service worker that was activated.

> public HRESULT [get_ActiveServiceWorker](#get_activeserviceworker)([ICoreWebView2ServiceWorker](icorewebview2serviceworker.md#icorewebview2serviceworker) ** value)

