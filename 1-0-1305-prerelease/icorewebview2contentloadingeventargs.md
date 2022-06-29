---
description: Event args for the `ContentLoading` event.
title: WebView2 Win32 C++ ICoreWebView2ContentLoadingEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContentLoadingEventArgs
---

# interface ICoreWebView2ContentLoadingEventArgs

```
interface ICoreWebView2ContentLoadingEventArgs
  : public IUnknown
```

Event args for the `ContentLoading` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsErrorPage](#get_iserrorpage) | `TRUE` if the loaded content is an error page.
[get_NavigationId](#get_navigationid) | The ID of the navigation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsErrorPage

`TRUE` if the loaded content is an error page.

> public HRESULT [get_IsErrorPage](#get_iserrorpage)(BOOL * isErrorPage)

#### get_NavigationId

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigationId)

