---
description: This is a continuation of the ICoreWebView2NewWindowRequestedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNewWindowRequestedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNewWindowRequestedEventArgs
---

# interface ICoreWebView2ExperimentalNewWindowRequestedEventArgs

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNewWindowRequestedEventArgs
  : public IUnknown
```

This is a continuation of the [ICoreWebView2NewWindowRequestedEventArgs](icorewebview2newwindowrequestedeventargs.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Name](#get_name) | Gets the name of the new window.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.538

## Members

#### get_Name

Gets the name of the new window.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

This window can be created via `window.open(url, windowName)`, where the windowName parameter corresponds to `Name` property. If no windowName is passed to `window.open`, then the `Name` property will be set to an empty string. Additionally, if window is opened through other means, such as `<a target="windowName">...</a>` or `<iframe name="windowName">...</iframe>`, then the `Name` property will be set accordingly. In the case of target=_blank, the `Name` property will be an empty string. Opening a window via ctrl+clicking a link would result in the `Name` property being set to an empty string.

