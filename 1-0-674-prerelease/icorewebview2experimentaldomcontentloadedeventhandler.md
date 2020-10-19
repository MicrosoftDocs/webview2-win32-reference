---
description: The caller implements this interface to receive the DOMContentLoaded event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDOMContentLoadedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/17/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDOMContentLoadedEventHandler
---

# interface ICoreWebView2ExperimentalDOMContentLoadedEventHandler 

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDOMContentLoadedEventHandler
  : public IUnknown
```

The caller implements this interface to receive the DOMContentLoaded event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

## Members

#### Invoke 

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2ExperimentalDOMContentLoadedEventArgs](icorewebview2experimentaldomcontentloadedeventargs.md) * args)

