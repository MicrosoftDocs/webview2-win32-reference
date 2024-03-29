---
description: The caller implements this interface to receive NewVersionAvailable events.
title: WebView2 Win32 C++ IWebView2NewVersionAvailableEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2NewVersionAvailableEventHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface IWebView2NewVersionAvailableEventHandler
  : public IUnknown
```

The caller implements this interface to receive NewVersionAvailable events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

Use the get_NewVersion method of [IWebView2NewVersionAvailableEventArgs](IWebView2NewVersionAvailableEventArgs.md) to get the new version number.

## Members

#### Invoke 

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([IWebView2Environment](IWebView2Environment.md) * webviewEnvironment,[IWebView2NewVersionAvailableEventArgs](IWebView2NewVersionAvailableEventArgs.md) * args)

