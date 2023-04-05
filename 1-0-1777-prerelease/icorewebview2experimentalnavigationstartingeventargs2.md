---
description: The NavigationKind API that enables developers to get more information about navigation type.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNavigationStartingEventArgs2
ms.date: 04/05/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNavigationStartingEventArgs2
---

# interface ICoreWebView2ExperimentalNavigationStartingEventArgs2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNavigationStartingEventArgs2
  : public IUnknown
```

The NavigationKind API that enables developers to get more information about navigation type.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_NavigationKind](#get_navigationkind) | Get the navigation kind of this navigation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1619

## Members

#### get_NavigationKind

Get the navigation kind of this navigation.

> public HRESULT [get_NavigationKind](#get_navigationkind)(COREWEBVIEW2_NAVIGATION_KIND * navigation_kind)

