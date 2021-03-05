---
description: ICoreWebView2Environment4 is a continuation of ICoreWebViewEnvironment interface.
title: WebView2 Win32 C++ ICoreWebView2Environment4
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 03/08/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment4
---

# interface ICoreWebView2Environment4 

```
interface ICoreWebView2Environment4
  : public ICoreWebView2Environment3
```

A continuation of ICoreWebViewEnvironment2 interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetProviderForHwnd](#getproviderforhwnd) | Returns the UI Automation Provider for the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) that corresponds with the given HWND.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    

## Members

#### GetProviderForHwnd 

Returns the UI Automation Provider for the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) that corresponds with the given HWND.

> public HRESULT [GetProviderForHwnd](#getproviderforhwnd)(HWND hwnd, IUnknown ** provider)

