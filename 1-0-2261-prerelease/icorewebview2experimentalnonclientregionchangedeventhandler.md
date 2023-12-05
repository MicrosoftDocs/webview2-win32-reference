---
description: This is the Interface of the event handler for the non-client region changed event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNonClientRegionChangedEventHandler
ms.date: 12/11/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNonClientRegionChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalNonClientRegionChangedEventHandler
- ICoreWebView2ExperimentalNonClientRegionChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalNonClientRegionChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNonClientRegionChangedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

This is the event handler for add_NonClientRegionChanged when executed, it recieves the event args.

> public HRESULT [Invoke](#invoke)(ICoreWebView2CompositionController * sender, ICoreWebView2ExperimentalNonClientRegionChangedEventArgs * args)

