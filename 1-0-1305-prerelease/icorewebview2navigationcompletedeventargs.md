---
description: Event args for the `NavigationCompleted` event.
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationCompletedEventArgs
---

# interface ICoreWebView2NavigationCompletedEventArgs

```
interface ICoreWebView2NavigationCompletedEventArgs
  : public IUnknown
```

Event args for the `NavigationCompleted` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSuccess](#get_issuccess) | `TRUE` when the navigation is successful.
[get_NavigationId](#get_navigationid) | The ID of the navigation.
[get_WebErrorStatus](#get_weberrorstatus) | The error code if the navigation failed.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsSuccess

`TRUE` when the navigation is successful.

> public HRESULT [get_IsSuccess](#get_issuccess)(BOOL * isSuccess)

`FALSE` for a navigation that ended up in an error page (failures due to no network, DNS lookup failure, HTTP server responds with 4xx), but may also be `FALSE` for additional scenarios such as `window.stop()` run on navigated page.

#### get_NavigationId

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigationId)

#### get_WebErrorStatus

The error code if the navigation failed.

> public HRESULT [get_WebErrorStatus](#get_weberrorstatus)(COREWEBVIEW2_WEB_ERROR_STATUS * webErrorStatus)

