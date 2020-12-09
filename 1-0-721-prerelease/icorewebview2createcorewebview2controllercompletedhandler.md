---
description: Receives the `CoreWebView2Controller` created using `CreateCoreWebView2Controller`.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/08/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
---

# interface ICoreWebView2CreateCoreWebView2ControllerCompletedHandler 

```
interface ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
  : public IUnknown
```

Receives the `CoreWebView2Controller` created using `CreateCoreWebView2Controller`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the completion status and result of the corresponding asynchronous method.

## Members

#### Invoke 

Provides the completion status and result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2Controller](icorewebview2controller.md) * createdController)

