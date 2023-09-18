---
description: 
title: WebView2 Win32 C++ ICoreWebView2BasicAuthenticationResponse
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BasicAuthenticationResponse
topic_type: 
- APIRef
api_name:
- ICoreWebView2BasicAuthenticationResponse
- ICoreWebView2BasicAuthenticationResponse.get_Password
- ICoreWebView2BasicAuthenticationResponse.get_UserName
- ICoreWebView2BasicAuthenticationResponse.put_Password
- ICoreWebView2BasicAuthenticationResponse.put_UserName
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BasicAuthenticationResponse

```
interface ICoreWebView2BasicAuthenticationResponse
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Password](#get_password) | Gets the `Password` property.
[get_UserName](#get_username) | Gets the `UserName` property.
[put_Password](#put_password) | Sets the `Password` property.
[put_UserName](#put_username) | Sets the `UserName` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_Password

Gets the `Password` property.

> public HRESULT [get_Password](#get_password)(LPWSTR * value)

#### get_UserName

Gets the `UserName` property.

> public HRESULT [get_UserName](#get_username)(LPWSTR * value)

#### put_Password

Sets the `Password` property.

> public HRESULT [put_Password](#put_password)(LPCWSTR value)

#### put_UserName

Sets the `UserName` property.

> public HRESULT [put_UserName](#put_username)(LPCWSTR value)

