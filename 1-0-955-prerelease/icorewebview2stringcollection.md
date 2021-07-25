---
description: A collection of strings.
title: WebView2 Win32 C++ ICoreWebView2StringCollection
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/26/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2StringCollection
---

# interface ICoreWebView2StringCollection

```
interface ICoreWebView2StringCollection
  : public IUnknown
```

A collection of strings.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of strings contained in [ICoreWebView2StringCollection](#icorewebview2stringcollection).
[GetValueAtIndex](#getvalueatindex) | Gets the value at a given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.955

## Members

#### get_Count

The number of strings contained in [ICoreWebView2StringCollection](#icorewebview2stringcollection).

> public HRESULT [get_Count](#get_count)(UINT * value)

#### GetValueAtIndex

Gets the value at a given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, LPWSTR * value)

