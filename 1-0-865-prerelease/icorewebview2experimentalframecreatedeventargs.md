---
description: Event args for the `FrameCreated` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameCreatedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameCreatedEventArgs
---

# interface ICoreWebView2ExperimentalFrameCreatedEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameCreatedEventArgs
  : public IUnknown
```

Event args for the `FrameCreated` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Frame](#get_frame) | The frame which was created.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### get_Frame

The frame which was created.

> public HRESULT [get_Frame](#get_frame)([ICoreWebView2ExperimentalFrame](icorewebview2experimentalframe.md) ** frame)

