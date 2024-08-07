---
description: Receives `ScreenCaptureStarting` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalScreenCaptureStartingEventHandler
ms.date: 07/31/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalScreenCaptureStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalScreenCaptureStartingEventHandler
- ICoreWebView2ExperimentalScreenCaptureStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalScreenCaptureStartingEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalScreenCaptureStartingEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ExperimentalScreenCaptureStartingEventArgs](icorewebview2experimentalscreencapturestartingeventargs.md#icorewebview2experimentalscreencapturestartingeventargs) * args)

