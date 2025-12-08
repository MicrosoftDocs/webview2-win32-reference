---
description: Receives `RasterizationScaleChanged` events.
title: WebView2 Win32 C++ ICoreWebView2RasterizationScaleChangedEventHandler
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2RasterizationScaleChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2RasterizationScaleChangedEventHandler
- ICoreWebView2RasterizationScaleChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2RasterizationScaleChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2RasterizationScaleChangedEventHandler
  : public IUnknown
```

Receives `RasterizationScaleChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Controller](icorewebview2controller.md#icorewebview2controller) * sender, IUnknown * args)

