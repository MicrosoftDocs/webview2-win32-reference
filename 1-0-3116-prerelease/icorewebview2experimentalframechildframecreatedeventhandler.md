---
description: Receives `FrameCreated` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameChildFrameCreatedEventHandler
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameChildFrameCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrameChildFrameCreatedEventHandler
- ICoreWebView2ExperimentalFrameChildFrameCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrameChildFrameCreatedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameChildFrameCreatedEventHandler
  : public IUnknown
```

Receives `FrameCreated` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2FrameCreatedEventArgs](icorewebview2framecreatedeventargs.md#icorewebview2framecreatedeventargs) * args)

