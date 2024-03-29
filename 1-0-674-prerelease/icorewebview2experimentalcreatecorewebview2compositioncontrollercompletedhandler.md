---
description: The caller implements this interface to receive the CoreWebView2Controller created via CreateCoreWebView2CompositionController.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCreateCoreWebView2CompositionControllerCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCreateCoreWebView2CompositionControllerCompletedHandler
---

# interface ICoreWebView2ExperimentalCreateCoreWebView2CompositionControllerCompletedHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCreateCoreWebView2CompositionControllerCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the CoreWebView2Controller created via CreateCoreWebView2CompositionController.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

## Members

#### Invoke 

Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalCompositionController](icorewebview2experimentalcompositioncontroller.md) * webView)

