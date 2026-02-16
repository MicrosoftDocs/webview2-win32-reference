---
description: Receives `DragStarting` events.
title: WebView2 Win32 C++ ICoreWebView2DragStartingEventHandler
ms.date: 02/09/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DragStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2DragStartingEventHandler
- ICoreWebView2DragStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DragStartingEventHandler

```
interface ICoreWebView2DragStartingEventHandler
  : public IUnknown
```

Receives `DragStarting` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3719.77
WebView2 Win32 Prerelease |    1.0.3712

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) * sender, [ICoreWebView2DragStartingEventArgs](icorewebview2dragstartingeventargs.md#icorewebview2dragstartingeventargs) * args)

