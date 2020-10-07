---
description: Additional functionality implemented by the primary WebView object.
title: WebView2 Win32 C++ IWebView2WebView2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2WebView2 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface IWebView2WebView2
  : public IUnknown
```

Additional functionality implemented by the primary WebView object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Stop](#stop) | Stop all navigations and pending resource fetches.

You can QueryInterface for this interface from the object that implements [IWebView2WebView](IWebView2WebView.md). See the [IWebView2WebView](IWebView2WebView.md) interface for more details.

## Members

#### Stop 

Stop all navigations and pending resource fetches.

> public HRESULT [Stop](#stop)()

