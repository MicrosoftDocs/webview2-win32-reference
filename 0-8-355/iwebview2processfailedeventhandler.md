---
description: The caller implements this interface to receive ProcessFailed events.
title: WebView2 Win32 C++ IWebView2ProcessFailedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2ProcessFailedEventHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface IWebView2ProcessFailedEventHandler
  : public IUnknown
```

The caller implements this interface to receive ProcessFailed events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

## Members

#### Invoke 

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([IWebView2WebView](IWebView2WebView.md) * webview,[IWebView2ProcessFailedEventArgs](IWebView2ProcessFailedEventArgs.md) * args)

