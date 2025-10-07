---
description: Interop interface for the CoreWebView2CompositionController WinRT object to allow WinRT end developers to be able to access the COM interface arguments.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCompositionControllerInterop3
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCompositionControllerInterop3
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalCompositionControllerInterop3
- ICoreWebView2ExperimentalCompositionControllerInterop3.add_DragStarting
- ICoreWebView2ExperimentalCompositionControllerInterop3.remove_DragStarting
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalCompositionControllerInterop3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCompositionControllerInterop3
  : public IUnknown
```

Interop interface for the CoreWebView2CompositionController WinRT object to allow WinRT end developers to be able to access the COM interface arguments.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DragStarting](#add_dragstarting) | Adds an event handler for the `DragStarting` event.
[remove_DragStarting](#remove_dragstarting) | Removes an event handler previously added with `add_DragStarting`.

This interface is implemented by the Microsoft.Web.WebView2.Core.CoreWebView2CompositionController runtime class.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### add_DragStarting

Adds an event handler for the `DragStarting` event.

> public HRESULT [add_DragStarting](#add_dragstarting)([ICoreWebView2ExperimentalDragStartingEventHandler](icorewebview2experimentaldragstartingeventhandler.md#icorewebview2experimentaldragstartingeventhandler) * eventHandler, EventRegistrationToken * token)

`DragStarting` is raised when the WebView2 detects a drag started within the WebView2. This event can be used to override WebView2's default drag starting logic.

#### remove_DragStarting

Removes an event handler previously added with `add_DragStarting`.

> public HRESULT [remove_DragStarting](#remove_dragstarting)(EventRegistrationToken token)

