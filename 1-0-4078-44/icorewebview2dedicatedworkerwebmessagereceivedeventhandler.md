---
description: Receives `WebMessageReceived` events.
title: WebView2 Win32 C++ ICoreWebView2DedicatedWorkerWebMessageReceivedEventHandler
ms.date: 06/30/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DedicatedWorkerWebMessageReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2DedicatedWorkerWebMessageReceivedEventHandler
- ICoreWebView2DedicatedWorkerWebMessageReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DedicatedWorkerWebMessageReceivedEventHandler

```
interface ICoreWebView2DedicatedWorkerWebMessageReceivedEventHandler
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
WebView2 Win32            |    1.0.4022.49
WebView2 Win32 Prerelease |    1.0.4015

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2DedicatedWorker](icorewebview2dedicatedworker.md#icorewebview2dedicatedworker) * sender, [ICoreWebView2WebMessageReceivedEventArgs](icorewebview2webmessagereceivedeventargs.md#icorewebview2webmessagereceivedeventargs) * args)

