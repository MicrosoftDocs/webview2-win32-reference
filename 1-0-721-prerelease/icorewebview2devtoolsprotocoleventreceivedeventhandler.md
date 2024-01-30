---
description: Receives `DevToolsProtocolEventReceived` events from the WebView.
title: WebView2 Win32 C++ ICoreWebView2DevToolsProtocolEventReceivedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/29/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DevToolsProtocolEventReceivedEventHandler
---

# interface ICoreWebView2DevToolsProtocolEventReceivedEventHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2DevToolsProtocolEventReceivedEventHandler
  : public IUnknown
```

Receives `DevToolsProtocolEventReceived` events from the WebView.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Members

#### Invoke 

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2DevToolsProtocolEventReceivedEventArgs * args)

