---
description: Receives `ServiceWorkerActivated` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler
- ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler
  : public IUnknown
```

Receives `ServiceWorkerActivated` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalServiceWorkerRegistration](icorewebview2experimentalserviceworkerregistration.md#icorewebview2experimentalserviceworkerregistration) * sender, [ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs](icorewebview2experimentalserviceworkeractivatedeventargs.md#icorewebview2experimentalserviceworkeractivatedeventargs) * args)

