---
description: 
title: WebView2 Win32 C++ ICoreWebView2ContentLoadingEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContentLoadingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ContentLoadingEventArgs
- ICoreWebView2ContentLoadingEventArgs.get_IsErrorPage
- ICoreWebView2ContentLoadingEventArgs.get_NavigationId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ContentLoadingEventArgs

```
interface ICoreWebView2ContentLoadingEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsErrorPage](#get_iserrorpage) | Gets the `IsErrorPage` property.
[get_NavigationId](#get_navigationid) | Gets the `NavigationId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsErrorPage

Gets the `IsErrorPage` property.

> public HRESULT [get_IsErrorPage](#get_iserrorpage)(BOOL * value)

#### get_NavigationId

Gets the `NavigationId` property.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * value)

