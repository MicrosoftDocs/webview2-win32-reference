---
description: Receives `DedicatedWorkerCreated` events.
title: WebView2 Win32 C++ ICoreWebView2FrameDedicatedWorkerCreatedEventHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameDedicatedWorkerCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameDedicatedWorkerCreatedEventHandler
- ICoreWebView2FrameDedicatedWorkerCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameDedicatedWorkerCreatedEventHandler

```
interface ICoreWebView2FrameDedicatedWorkerCreatedEventHandler
  : public IUnknown
```

Receives `DedicatedWorkerCreated` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2DedicatedWorkerCreatedEventArgs](icorewebview2dedicatedworkercreatedeventargs.md#icorewebview2dedicatedworkercreatedeventargs) * args)

