---
description: Receives `Unregistering` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler
- ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler
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
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalServiceWorkerRegistration](icorewebview2experimentalserviceworkerregistration.md#icorewebview2experimentalserviceworkerregistration) * sender, IUnknown * args)

