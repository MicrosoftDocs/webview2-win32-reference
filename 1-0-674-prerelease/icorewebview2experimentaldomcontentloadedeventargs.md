---
description: Event args for the DOMContentLoaded event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDOMContentLoadedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/19/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDOMContentLoadedEventArgs
---

# interface ICoreWebView2ExperimentalDOMContentLoadedEventArgs 

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDOMContentLoadedEventArgs
  : public IUnknown
```

Event args for the DOMContentLoaded event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_NavigationId](#get_navigationid) | The ID of the navigation.

## Members

#### get_NavigationId 

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigation_id)

