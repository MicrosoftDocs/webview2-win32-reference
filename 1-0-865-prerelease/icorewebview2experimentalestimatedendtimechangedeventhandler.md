---
description: Implements the interface to receive `EstimatedEndTimeChanged` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEstimatedEndTimeChangedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/01/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEstimatedEndTimeChangedEventHandler
---

# interface ICoreWebView2ExperimentalEstimatedEndTimeChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEstimatedEndTimeChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `EstimatedEndTimeChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the `ICoreWebView2DownloadOperation.EstimatedEndTime` property to get the new estimated end time.

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

