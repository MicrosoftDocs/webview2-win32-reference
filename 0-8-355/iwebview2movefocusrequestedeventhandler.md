---
description: The caller implements this method to receive the MoveFocusRequested event.
title: WebView2 Win32 C++ IWebView2MoveFocusRequestedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2MoveFocusRequestedEventHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface IWebView2MoveFocusRequestedEventHandler
  : public IUnknown
```

The caller implements this method to receive the MoveFocusRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

## Members

#### Invoke 

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([IWebView2WebView](IWebView2WebView.md) * webview,[IWebView2MoveFocusRequestedEventArgs](IWebView2MoveFocusRequestedEventArgs.md) * args)

