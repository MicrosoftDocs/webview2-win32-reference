---
description: Receives `DragStarting` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDragStartingEventHandler
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDragStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDragStartingEventHandler
- ICoreWebView2ExperimentalDragStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDragStartingEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDragStartingEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) * sender, [ICoreWebView2ExperimentalDragStartingEventArgs](icorewebview2experimentaldragstartingeventargs.md#icorewebview2experimentaldragstartingeventargs) * args)

