---
description: Receives `DOMContentLoaded` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameDOMContentLoadedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameDOMContentLoadedEventHandler
---

# interface ICoreWebView2ExperimentalFrameDOMContentLoadedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameDOMContentLoadedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md) * sender, [ICoreWebView2DOMContentLoadedEventArgs](icorewebview2domcontentloadedeventargs.md) * args)

