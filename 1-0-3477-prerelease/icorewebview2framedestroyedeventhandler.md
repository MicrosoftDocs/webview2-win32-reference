---
description: Receives `Destroyed` events.
title: WebView2 Win32 C++ ICoreWebView2FrameDestroyedEventHandler
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameDestroyedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameDestroyedEventHandler
- ICoreWebView2FrameDestroyedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameDestroyedEventHandler

```
interface ICoreWebView2FrameDestroyedEventHandler
  : public IUnknown
```

Receives `Destroyed` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, IUnknown * args)

