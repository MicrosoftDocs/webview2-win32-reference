---
description: Event args for the `NavigationCompleted` event.
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventArgs
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationCompletedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationCompletedEventArgs
- ICoreWebView2NavigationCompletedEventArgs.get_IsSuccess
- ICoreWebView2NavigationCompletedEventArgs.get_NavigationId
- ICoreWebView2NavigationCompletedEventArgs.get_WebErrorStatus
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
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

`FALSE` for a navigation that ended up in an error page (failures due to no network, DNS lookup failure, HTTP server responds with 4xx), but may also be `FALSE` for additional scenarios such as `window.stop()` run on navigated page. Note that WebView2 will report the navigation as 'unsuccessful' if the load for the navigation did not reach the expected completion for any reason. Such reasons include potentially catastrophic issues such network and certificate issues, but can also be the result of intended actions such as the app canceling a navigation or navigating away before the original navigation completed. Applications should not just rely on this flag, but also consider the reported WebErrorStatus to determine whether the failure is indeed catastrophic in their context. WebErrorStatuses that may indicate a non-catastrophic failure include:

* COREWEBVIEW2_WEB_ERROR_STATUS_OPERATION_CANCELED

* COREWEBVIEW2_WEB_ERROR_STATUS_VALID_AUTHENTICATION_CREDENTIALS_REQUIRED

* COREWEBVIEW2_WEB_ERROR_STATUS_VALID_PROXY_AUTHENTICATION_REQUIRED

#### get_NavigationId

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigationId)

#### get_WebErrorStatus

The error code if the navigation failed.

> public HRESULT [get_WebErrorStatus](#get_weberrorstatus)(COREWEBVIEW2_WEB_ERROR_STATUS * webErrorStatus)

