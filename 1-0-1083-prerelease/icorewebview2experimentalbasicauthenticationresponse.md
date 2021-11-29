---
description: Represents a Basic HTTP authentication response that contains a user name and a password as according to RFC7617 (https://tools.ietf.org/html/rfc7617)
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBasicAuthenticationResponse
ms.date: 11/29/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBasicAuthenticationResponse
---

# interface ICoreWebView2ExperimentalBasicAuthenticationResponse

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBasicAuthenticationResponse
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### get_Password

Password provided for authentication.

> public HRESULT [get_Password](#get_password)(LPWSTR * password)

#### get_UserName

User name provided for authentication.

> public HRESULT [get_UserName](#get_username)(LPWSTR * userName)

#### put_Password

Set password property.

> public HRESULT [put_Password](#put_password)(LPCWSTR password)

#### put_UserName

Set user name property.

> public HRESULT [put_UserName](#put_username)(LPCWSTR userName)

