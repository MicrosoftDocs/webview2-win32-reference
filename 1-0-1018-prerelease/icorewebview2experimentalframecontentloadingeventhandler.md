---
description: Receives `ContentLoading` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameContentLoadingEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameContentLoadingEventHandler
---

# interface ICoreWebView2ExperimentalFrameContentLoadingEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameContentLoadingEventHandler
  : public IUnknown
```

Receives `ContentLoading` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md) * sender, [ICoreWebView2ContentLoadingEventArgs](icorewebview2contentloadingeventargs.md) * args)

