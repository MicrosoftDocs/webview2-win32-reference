---
description: Receives `SaveAsUIShowing` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSaveAsUIShowingEventHandler
ms.date: 06/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSaveAsUIShowingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSaveAsUIShowingEventHandler
- ICoreWebView2ExperimentalSaveAsUIShowingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSaveAsUIShowingEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSaveAsUIShowingEventHandler
  : public IUnknown
```

Receives `SaveAsUIShowing` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2526

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ExperimentalSaveAsUIShowingEventArgs](icorewebview2experimentalsaveasuishowingeventargs.md#icorewebview2experimentalsaveasuishowingeventargs) * args)

