---
description: Receives `FrameCreated` events.
title: WebView2 Win32 C++ ICoreWebView2FrameChildFrameCreatedEventHandler
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameChildFrameCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameChildFrameCreatedEventHandler
- ICoreWebView2FrameChildFrameCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameChildFrameCreatedEventHandler

```
interface ICoreWebView2FrameChildFrameCreatedEventHandler
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
WebView2 Win32            |    1.0.3240.44
WebView2 Win32 Prerelease |    1.0.3230

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2FrameCreatedEventArgs](icorewebview2framecreatedeventargs.md#icorewebview2framecreatedeventargs) * args)

