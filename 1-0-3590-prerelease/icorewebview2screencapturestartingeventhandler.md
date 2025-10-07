---
description: Receives `ScreenCaptureStarting` events.
title: WebView2 Win32 C++ ICoreWebView2ScreenCaptureStartingEventHandler
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ScreenCaptureStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ScreenCaptureStartingEventHandler
- ICoreWebView2ScreenCaptureStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ScreenCaptureStartingEventHandler

```
interface ICoreWebView2ScreenCaptureStartingEventHandler
  : public IUnknown
```

Receives `ScreenCaptureStarting` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2903.40
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ScreenCaptureStartingEventArgs](icorewebview2screencapturestartingeventargs.md#icorewebview2screencapturestartingeventargs) * args)

