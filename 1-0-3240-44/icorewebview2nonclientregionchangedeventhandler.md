---
description: Receives `NonClientRegionChanged` events.
title: WebView2 Win32 C++ ICoreWebView2NonClientRegionChangedEventHandler
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NonClientRegionChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NonClientRegionChangedEventHandler
- ICoreWebView2NonClientRegionChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NonClientRegionChangedEventHandler

```
interface ICoreWebView2NonClientRegionChangedEventHandler
  : public IUnknown
```

Receives `NonClientRegionChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2420.47
WebView2 Win32 Prerelease |    1.0.2415

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) * sender, [ICoreWebView2NonClientRegionChangedEventArgs](icorewebview2nonclientregionchangedeventargs.md#icorewebview2nonclientregionchangedeventargs) * args)

