---
description: Receives `WebMessageReceived` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler
- ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler
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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalDedicatedWorker](icorewebview2experimentaldedicatedworker.md#icorewebview2experimentaldedicatedworker) * sender, [ICoreWebView2WebMessageReceivedEventArgs](icorewebview2webmessagereceivedeventargs.md#icorewebview2webmessagereceivedeventargs) * args)

