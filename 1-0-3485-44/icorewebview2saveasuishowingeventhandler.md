---
description: Receives `SaveAsUIShowing` events.
title: WebView2 Win32 C++ ICoreWebView2SaveAsUIShowingEventHandler
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SaveAsUIShowingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2SaveAsUIShowingEventHandler
- ICoreWebView2SaveAsUIShowingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SaveAsUIShowingEventHandler

```
interface ICoreWebView2SaveAsUIShowingEventHandler
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
WebView2 Win32            |    1.0.2739.15
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2SaveAsUIShowingEventArgs](icorewebview2saveasuishowingeventargs.md#icorewebview2saveasuishowingeventargs) * args)

