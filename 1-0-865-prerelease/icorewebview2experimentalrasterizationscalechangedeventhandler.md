---
description: The caller implements this interface to receive RasterizationScaleChanged events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalRasterizationScaleChangedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/23/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalRasterizationScaleChangedEventHandler
---

# interface ICoreWebView2ExperimentalRasterizationScaleChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalRasterizationScaleChangedEventHandler
  : public IUnknown
```

The caller implements this interface to receive RasterizationScaleChanged events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

Use the ICoreWebView2ExperimentalController.RasterizationScale property to get the modified rasterization scale.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.721

## Members

#### Invoke

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalController](icorewebview2experimentalcontroller.md) * sender, IUnknown * args)

There are no event args and the args parameter will be null.

