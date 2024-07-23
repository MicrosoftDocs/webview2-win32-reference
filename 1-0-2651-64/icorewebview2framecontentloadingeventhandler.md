---
description: Receives `ContentLoading` events.
title: WebView2 Win32 C++ ICoreWebView2FrameContentLoadingEventHandler
ms.date: 07/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameContentLoadingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameContentLoadingEventHandler
- ICoreWebView2FrameContentLoadingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameContentLoadingEventHandler

```
interface ICoreWebView2FrameContentLoadingEventHandler
  : public IUnknown
```

Receives `ContentLoading` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2ContentLoadingEventArgs](icorewebview2contentloadingeventargs.md#icorewebview2contentloadingeventargs) * args)

