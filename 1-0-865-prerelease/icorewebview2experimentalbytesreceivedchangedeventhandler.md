---
description: Implements the interface to receive `BytesReceivedChanged` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBytesReceivedChangedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBytesReceivedChangedEventHandler
---

# interface ICoreWebView2ExperimentalBytesReceivedChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBytesReceivedChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `BytesReceivedChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the `ICoreWebView2DownloadOperation.BytesReceived` property to get the received bytes count.

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

