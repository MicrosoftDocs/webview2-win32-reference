---
description: Receives `WebResourceResponseReceived` events.
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponseReceivedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/15/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponseReceivedEventHandler
---

# interface ICoreWebView2WebResourceResponseReceivedEventHandler

```
interface ICoreWebView2WebResourceResponseReceivedEventHandler
  : public IUnknown
```

Receives `WebResourceResponseReceived` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2WebResourceResponseReceivedEventArgs](icorewebview2webresourceresponsereceivedeventargs.md) * args)

