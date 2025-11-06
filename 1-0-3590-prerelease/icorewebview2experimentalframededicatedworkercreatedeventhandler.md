---
description: Receives `DedicatedWorkerCreated` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameDedicatedWorkerCreatedEventHandler
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameDedicatedWorkerCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrameDedicatedWorkerCreatedEventHandler
- ICoreWebView2ExperimentalFrameDedicatedWorkerCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrameDedicatedWorkerCreatedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameDedicatedWorkerCreatedEventHandler
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
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs](icorewebview2experimentaldedicatedworkercreatedeventargs.md#icorewebview2experimentaldedicatedworkercreatedeventargs) * args)

