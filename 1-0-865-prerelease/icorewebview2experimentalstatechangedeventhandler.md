---
description: Implements the interface to receive `StateChanged` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalStateChangedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/23/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalStateChangedEventHandler
---

# interface ICoreWebView2ExperimentalStateChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalStateChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `StateChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the `ICoreWebView2DownloadOperation.State` property to get the current state, which can be in progress, interrupted, or completed. Use the `ICoreWebView2DownloadOperation.InterruptReason` property to get the interrupt reason if the download is interrupted.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalDownloadOperation](icorewebview2experimentaldownloadoperation.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

