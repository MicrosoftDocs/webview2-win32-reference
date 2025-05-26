---
description: Receives `ContainsFullScreenElementChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ContainsFullScreenElementChangedEventHandler
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContainsFullScreenElementChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ContainsFullScreenElementChangedEventHandler
- ICoreWebView2ContainsFullScreenElementChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ContainsFullScreenElementChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ContainsFullScreenElementChangedEventHandler
  : public IUnknown
```

Receives `ContainsFullScreenElementChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, IUnknown * args)

