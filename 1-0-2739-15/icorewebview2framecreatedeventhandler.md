---
description: Receives `FrameCreated` events.
title: WebView2 Win32 C++ ICoreWebView2FrameCreatedEventHandler
ms.date: 08/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameCreatedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameCreatedEventHandler
- ICoreWebView2FrameCreatedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameCreatedEventHandler

```
interface ICoreWebView2FrameCreatedEventHandler
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
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2FrameCreatedEventArgs](icorewebview2framecreatedeventargs.md#icorewebview2framecreatedeventargs) * args)

