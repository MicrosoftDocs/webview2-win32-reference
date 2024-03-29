---
description: Event args for the NavigationCompleted event.
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/29/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationCompletedEventArgs
---

# interface ICoreWebView2NavigationCompletedEventArgs 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NavigationCompletedEventArgs
  : public IUnknown
```

Event args for the NavigationCompleted event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSuccess](#get_issuccess) | True when the navigation is successful.
[get_NavigationId](#get_navigationid) | The ID of the navigation.
[get_WebErrorStatus](#get_weberrorstatus) | The error code if the navigation failed.

## Members

#### get_IsSuccess 

True when the navigation is successful.

> public HRESULT [get_IsSuccess](#get_issuccess)(BOOL * isSuccess)

This is false for a navigation that ended up in an error page (failures due to no network, DNS lookup failure, HTTP server responds with 4xx), but could also be false for additional scenarios such as window.stop() called on navigated page.

#### get_NavigationId 

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigationId)

#### get_WebErrorStatus 

The error code if the navigation failed.

> public HRESULT [get_WebErrorStatus](#get_weberrorstatus)(COREWEBVIEW2_WEB_ERROR_STATUS * webErrorStatus)

