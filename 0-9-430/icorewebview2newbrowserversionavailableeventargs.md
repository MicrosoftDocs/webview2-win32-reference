---
description: Event args for the NewBrowserVersionAvailable event.
title: WebView2 Win32 C++ ICoreWebView2NewBrowserVersionAvailableEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Host, browser control, edge html
---

# interface ICoreWebView2NewBrowserVersionAvailableEventArgs 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NewBrowserVersionAvailableEventArgs
  : public IUnknown
```

Event args for the NewBrowserVersionAvailable event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_NewVersion](#get_newversion) | The browser version info of the current [ICoreWebView2Environment](ICoreWebView2Environment.md).

## Members

#### get_NewVersion 

The browser version info of the current [ICoreWebView2Environment](ICoreWebView2Environment.md).

> public HRESULT [get_NewVersion](#get_newversion)(LPWSTR * newVersion)

