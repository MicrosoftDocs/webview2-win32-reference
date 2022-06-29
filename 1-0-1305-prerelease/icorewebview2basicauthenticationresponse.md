---
description: Represents a Basic HTTP authentication response that contains a user name and a password as according to RFC7617 (https://tools.ietf.org/html/rfc7617)
title: WebView2 Win32 C++ ICoreWebView2BasicAuthenticationResponse
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BasicAuthenticationResponse
---

# interface ICoreWebView2BasicAuthenticationResponse

```
interface ICoreWebView2BasicAuthenticationResponse
  : public IUnknown
```

Represents a Basic HTTP authentication response that contains a user name and a password as according to RFC7617 (https://tools.ietf.org/html/rfc7617)

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Password](#get_password) | Password provided for authentication.
[get_UserName](#get_username) | User name provided for authentication.
[put_Password](#put_password) | Set password property.
[put_UserName](#put_username) | Set user name property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_Password

Password provided for authentication.

> public HRESULT [get_Password](#get_password)(LPWSTR * password)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_UserName

User name provided for authentication.

> public HRESULT [get_UserName](#get_username)(LPWSTR * userName)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_Password

Set password property.

> public HRESULT [put_Password](#put_password)(LPCWSTR password)

#### put_UserName

Set user name property.

> public HRESULT [put_UserName](#put_username)(LPCWSTR userName)

