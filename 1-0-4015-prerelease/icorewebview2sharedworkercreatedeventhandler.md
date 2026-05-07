---
description: Receives `SharedWorkerCreated` events.
title: WebView2 Win32 C++ ICoreWebView2SharedWorkerCreatedEventHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SharedWorkerCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2SharedWorkerCreatedEventHandler
- ICoreWebView2SharedWorkerCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SharedWorkerCreatedEventHandler

```
interface ICoreWebView2SharedWorkerCreatedEventHandler
  : public IUnknown
```

Receives `SharedWorkerCreated` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2SharedWorkerManager](icorewebview2sharedworkermanager.md#icorewebview2sharedworkermanager) * sender, [ICoreWebView2SharedWorkerCreatedEventArgs](icorewebview2sharedworkercreatedeventargs.md#icorewebview2sharedworkercreatedeventargs) * args)

