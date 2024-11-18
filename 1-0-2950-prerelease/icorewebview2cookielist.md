---
description: A collection of ICoreWebView2Cookie.
title: WebView2 Win32 C++ ICoreWebView2CookieList
ms.date: 11/11/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CookieList
topic_type: 
- APIRef
api_name:
- ICoreWebView2CookieList
- ICoreWebView2CookieList.get_Count
- ICoreWebView2CookieList.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CookieList

```
interface ICoreWebView2CookieList
  : public IUnknown
```

A collection of [ICoreWebView2Cookie](icorewebview2cookie.md#icorewebview2cookie).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2Cookie](icorewebview2cookie.md#icorewebview2cookie) ** value)

