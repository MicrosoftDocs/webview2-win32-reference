---
description: Receives `FaviconChanged` events.
title: WebView2 Win32 C++ ICoreWebView2FaviconChangedEventHandler
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FaviconChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FaviconChangedEventHandler
- ICoreWebView2FaviconChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FaviconChangedEventHandler

```
interface ICoreWebView2FaviconChangedEventHandler
  : public IUnknown
```

Receives `FaviconChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1293.44
WebView2 Win32 Prerelease |    1.0.1305

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, IUnknown * args)

