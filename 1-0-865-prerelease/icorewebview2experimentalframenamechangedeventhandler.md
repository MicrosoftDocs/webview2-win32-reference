---
description: Receives `FrameNameChanged` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameNameChangedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/23/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameNameChangedEventHandler
---

# interface ICoreWebView2ExperimentalFrameNameChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameNameChangedEventHandler
  : public IUnknown
```

Receives `FrameNameChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result for the iframe name changed event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### Invoke

Provides the result for the iframe name changed event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalFrame](icorewebview2experimentalframe.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

