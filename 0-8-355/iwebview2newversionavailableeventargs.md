---
description: Event args for the NewVersionAvailable event.
title: WebView2 Win32 C++ IWebView2NewVersionAvailableEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge
---

# interface IWebView2NewVersionAvailableEventArgs 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface IWebView2NewVersionAvailableEventArgs
  : public IUnknown
```

Event args for the NewVersionAvailable event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_NewVersion](#get_newversion) | The browser version info of the current [IWebView2Environment](IWebView2Environment.md).

## Members

#### get_NewVersion 

The browser version info of the current [IWebView2Environment](IWebView2Environment.md).

> public HRESULT [get_NewVersion](#get_newversion)(LPWSTR * newVersion)

