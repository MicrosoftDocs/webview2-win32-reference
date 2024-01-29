---
description: Receives `FrameDestroyed` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameDestroyedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameDestroyedEventHandler
---

# interface ICoreWebView2ExperimentalFrameDestroyedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameDestroyedEventHandler
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
WebView2 Win32 Prerelease |    1.0.865

## Members

#### Invoke

Provides the result for the iframe destroyed event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalFrame](icorewebview2experimentalframe.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

