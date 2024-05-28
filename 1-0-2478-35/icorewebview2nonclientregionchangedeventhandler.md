---
description: This is the Interface of the event handler for the non-client region changed event.
title: WebView2 Win32 C++ ICoreWebView2NonClientRegionChangedEventHandler
ms.date: 05/20/2024
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NonClientRegionChangedEventHandler
  : public IUnknown
```

This is the Interface of the event handler for the non-client region changed event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | This is the event handler for add_NonClientRegionChanged when executed, it recieves the event args.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2420.47
WebView2 Win32 Prerelease |    1.0.2415

## Members

#### Invoke

This is the event handler for add_NonClientRegionChanged when executed, it recieves the event args.

> public HRESULT [Invoke](#invoke)([ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) * sender, [ICoreWebView2NonClientRegionChangedEventArgs](icorewebview2nonclientregionchangedeventargs.md#icorewebview2nonclientregionchangedeventargs) * args)

