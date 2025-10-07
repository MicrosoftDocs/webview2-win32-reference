---
description: Receives `WebMessageReceived` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler
- ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler
  : public IUnknown
```

Receives `WebMessageReceived` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalServiceWorker](icorewebview2experimentalserviceworker.md#icorewebview2experimentalserviceworker) * sender, [ICoreWebView2WebMessageReceivedEventArgs](icorewebview2webmessagereceivedeventargs.md#icorewebview2webmessagereceivedeventargs) * args)

