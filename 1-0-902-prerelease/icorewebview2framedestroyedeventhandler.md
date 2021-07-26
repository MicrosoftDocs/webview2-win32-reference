---
description: Receives `FrameDestroyed` event.
title: WebView2 Win32 C++ ICoreWebView2FrameDestroyedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/26/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameDestroyedEventHandler
---

# interface ICoreWebView2FrameDestroyedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2FrameDestroyedEventHandler
  : public IUnknown
```

Receives `FrameDestroyed` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result for the iframe destroyed event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the result for the iframe destroyed event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

