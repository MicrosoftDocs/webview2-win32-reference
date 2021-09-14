---
description: A continuation of the ICoreWebView2CompositionController interface.
title: WebView2 Win32 C++ ICoreWebView2CompositionController2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController2
---

# interface ICoreWebView2CompositionController2

```
interface ICoreWebView2CompositionController2
  : public ICoreWebView2CompositionController
```

A continuation of the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UIAProvider](#get_uiaprovider) | Returns the UI Automation Provider for the WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_UIAProvider

Returns the UI Automation Provider for the WebView.

> public HRESULT [get_UIAProvider](#get_uiaprovider)(IUnknown ** provider)

