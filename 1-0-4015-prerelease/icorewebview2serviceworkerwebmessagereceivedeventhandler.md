---
description: Receives `WebMessageReceived` events.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerWebMessageReceivedEventHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerWebMessageReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerWebMessageReceivedEventHandler
- ICoreWebView2ServiceWorkerWebMessageReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerWebMessageReceivedEventHandler

```
interface ICoreWebView2ServiceWorkerWebMessageReceivedEventHandler
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
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ServiceWorker](icorewebview2serviceworker.md#icorewebview2serviceworker) * sender, [ICoreWebView2WebMessageReceivedEventArgs](icorewebview2webmessagereceivedeventargs.md#icorewebview2webmessagereceivedeventargs) * args)

