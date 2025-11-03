---
description: Receives `DOMContentLoaded` events.
title: WebView2 Win32 C++ ICoreWebView2DOMContentLoadedEventHandler
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DOMContentLoadedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2DOMContentLoadedEventHandler
- ICoreWebView2DOMContentLoadedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DOMContentLoadedEventHandler

```
interface ICoreWebView2DOMContentLoadedEventHandler
  : public IUnknown
```

Receives `DOMContentLoaded` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2DOMContentLoadedEventArgs](icorewebview2domcontentloadedeventargs.md#icorewebview2domcontentloadedeventargs) * args)

