---
description: The NavigationKind API that enables developers to get more information about navigation type.
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventArgs3
ms.date: 07/24/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventArgs3
---

# interface ICoreWebView2NavigationStartingEventArgs3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NavigationStartingEventArgs3
  : public ICoreWebView2NavigationStartingEventArgs2
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
WebView2 Win32 Prerelease |    

## Members

#### get_NavigationKind

Get the navigation kind of this navigation.

> public HRESULT [get_NavigationKind](#get_navigationkind)(COREWEBVIEW2_NAVIGATION_KIND * navigation_kind)

