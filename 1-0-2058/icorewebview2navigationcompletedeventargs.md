---
description: 
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventArgs
ms.date: 09/08/2023
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

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSuccess](#get_issuccess) | Gets the `IsSuccess` property.
[get_NavigationId](#get_navigationid) | Gets the `NavigationId` property.
[get_WebErrorStatus](#get_weberrorstatus) | Gets the `WebErrorStatus` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsSuccess

Gets the `IsSuccess` property.

> public HRESULT [get_IsSuccess](#get_issuccess)(BOOL * value)

#### get_NavigationId

Gets the `NavigationId` property.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * value)

#### get_WebErrorStatus

Gets the `WebErrorStatus` property.

> public HRESULT [get_WebErrorStatus](#get_weberrorstatus)(COREWEBVIEW2_WEB_ERROR_STATUS * value)

