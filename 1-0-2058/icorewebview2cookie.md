---
description: 
title: WebView2 Win32 C++ ICoreWebView2Cookie
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Cookie
topic_type: 
- APIRef
api_name:
- ICoreWebView2Cookie
- ICoreWebView2Cookie.get_Domain
- ICoreWebView2Cookie.get_Expires
- ICoreWebView2Cookie.get_IsHttpOnly
- ICoreWebView2Cookie.get_IsSecure
- ICoreWebView2Cookie.get_IsSession
- ICoreWebView2Cookie.get_Name
- ICoreWebView2Cookie.get_Path
- ICoreWebView2Cookie.get_SameSite
- ICoreWebView2Cookie.get_Value
- ICoreWebView2Cookie.put_Expires
- ICoreWebView2Cookie.put_IsHttpOnly
- ICoreWebView2Cookie.put_IsSecure
- ICoreWebView2Cookie.put_SameSite
- ICoreWebView2Cookie.put_Value
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Cookie

```
interface ICoreWebView2Cookie
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Domain](#get_domain) | Gets the `Domain` property.
[get_Expires](#get_expires) | Gets the `Expires` property.
[get_IsHttpOnly](#get_ishttponly) | Gets the `IsHttpOnly` property.
[get_IsSecure](#get_issecure) | Gets the `IsSecure` property.
[get_IsSession](#get_issession) | Gets the `IsSession` property.
[get_Name](#get_name) | Gets the `Name` property.
[get_Path](#get_path) | Gets the `Path` property.
[get_SameSite](#get_samesite) | Gets the `SameSite` property.
[get_Value](#get_value) | Gets the `Value` property.
[put_Expires](#put_expires) | Sets the `Expires` property.
[put_IsHttpOnly](#put_ishttponly) | Sets the `IsHttpOnly` property.
[put_IsSecure](#put_issecure) | Sets the `IsSecure` property.
[put_SameSite](#put_samesite) | Sets the `SameSite` property.
[put_Value](#put_value) | Sets the `Value` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Domain

Gets the `Domain` property.

> public HRESULT [get_Domain](#get_domain)(LPWSTR * value)

#### get_Expires

Gets the `Expires` property.

> public HRESULT [get_Expires](#get_expires)(double * value)

#### get_IsHttpOnly

Gets the `IsHttpOnly` property.

> public HRESULT [get_IsHttpOnly](#get_ishttponly)(BOOL * value)

#### get_IsSecure

Gets the `IsSecure` property.

> public HRESULT [get_IsSecure](#get_issecure)(BOOL * value)

#### get_IsSession

Gets the `IsSession` property.

> public HRESULT [get_IsSession](#get_issession)(BOOL * value)

#### get_Name

Gets the `Name` property.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

#### get_Path

Gets the `Path` property.

> public HRESULT [get_Path](#get_path)(LPWSTR * value)

#### get_SameSite

Gets the `SameSite` property.

> public HRESULT [get_SameSite](#get_samesite)(COREWEBVIEW2_COOKIE_SAME_SITE_KIND * value)

#### get_Value

Gets the `Value` property.

> public HRESULT [get_Value](#get_value)(LPWSTR * value)

#### put_Expires

Sets the `Expires` property.

> public HRESULT [put_Expires](#put_expires)(double value)

#### put_IsHttpOnly

Sets the `IsHttpOnly` property.

> public HRESULT [put_IsHttpOnly](#put_ishttponly)(BOOL value)

#### put_IsSecure

Sets the `IsSecure` property.

> public HRESULT [put_IsSecure](#put_issecure)(BOOL value)

#### put_SameSite

Sets the `SameSite` property.

> public HRESULT [put_SameSite](#put_samesite)(COREWEBVIEW2_COOKIE_SAME_SITE_KIND value)

#### put_Value

Sets the `Value` property.

> public HRESULT [put_Value](#put_value)(LPCWSTR value)

