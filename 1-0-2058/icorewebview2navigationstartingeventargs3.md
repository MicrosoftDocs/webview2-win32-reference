---
description: 
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventArgs3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventArgs3
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationStartingEventArgs3
- ICoreWebView2NavigationStartingEventArgs3.get_NavigationKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NavigationStartingEventArgs3

```
interface ICoreWebView2NavigationStartingEventArgs3
  : public ICoreWebView2NavigationStartingEventArgs2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_NavigationKind](#get_navigationkind) | Gets the `NavigationKind` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1901.177
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### get_NavigationKind

Gets the `NavigationKind` property.

> public HRESULT [get_NavigationKind](#get_navigationkind)(COREWEBVIEW2_NAVIGATION_KIND * value)

