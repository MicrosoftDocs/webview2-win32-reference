---
description: ICoreWebView2CompositionController2 is a continuation of the ICoreWebView2CompositionController interface.
title: WebView2 Win32 C++ ICoreWebView2CompositionController2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/08/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController2
---

# interface ICoreWebView2CompositionController2 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

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
WebView2 Win32 Prerelease |    

## Members

#### get_UIAProvider 

Returns the UI Automation Provider for the WebView.

> public HRESULT [get_UIAProvider](#get_uiaprovider)(IUnknown ** provider)

