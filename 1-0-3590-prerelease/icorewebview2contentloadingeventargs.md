---
description: Event args for the `ContentLoading` event.
title: WebView2 Win32 C++ ICoreWebView2ContentLoadingEventArgs
ms.date: 10/01/2025
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

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

> public HRESULT [get_IsErrorPage](#get_iserrorpage)(BOOL * value)

#### get_NavigationId

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * value)

