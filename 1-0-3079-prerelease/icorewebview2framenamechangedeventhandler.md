---
description: Receives `NameChanged` events.
title: WebView2 Win32 C++ ICoreWebView2FrameNameChangedEventHandler
ms.date: 01/16/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameNameChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameNameChangedEventHandler
- ICoreWebView2FrameNameChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameNameChangedEventHandler

```
interface ICoreWebView2FrameNameChangedEventHandler
  : public IUnknown
```

Receives `NameChanged` events.

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

