---
description: Provides a set of properties that are used to manage an ICoreWebView2Cookie.
title: WebView2 Win32 C++ ICoreWebView2Cookie
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Cookie
---

# interface ICoreWebView2Cookie

```
interface ICoreWebView2Cookie
  : public IUnknown
```

Provides a set of properties that are used to manage an ICoreWebView2Cookie.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Domain](#get_domain) | The domain for which the cookie is valid.
[get_Expires](#get_expires) | The expiration date and time for the cookie as the number of seconds since the UNIX epoch.
[get_IsHttpOnly](#get_ishttponly) | Whether this cookie is http-only.
[get_IsSecure](#get_issecure) | The security level of this cookie.
[get_IsSession](#get_issession) | Whether this is a session cookie. The default is false.
[get_Name](#get_name) | Cookie name.
[get_Path](#get_path) | The path for which the cookie is valid.
[get_SameSite](#get_samesite) | SameSite status of the cookie which represents the enforcement mode of the cookie.
[get_Value](#get_value) | Cookie value.
[put_Expires](#put_expires) | Set the Expires property.
[put_IsHttpOnly](#put_ishttponly) | Set the IsHttpOnly property.
[put_IsSecure](#put_issecure) | Set the IsSecure property.
[put_SameSite](#put_samesite) | Set the SameSite property.
[put_Value](#put_value) | Set the cookie value property.

```cpp
    wil::unique_cotaskmem_string name;
    CHECK_FAILURE(cookie->get_Name(&name));
    wil::unique_cotaskmem_string value;
    CHECK_FAILURE(cookie->get_Value(&value));
    wil::unique_cotaskmem_string domain;
    CHECK_FAILURE(cookie->get_Domain(&domain));
    wil::unique_cotaskmem_string path;
    CHECK_FAILURE(cookie->get_Path(&path));
    double expires;
    CHECK_FAILURE(cookie->get_Expires(&expires));
    BOOL isHttpOnly = FALSE;
    CHECK_FAILURE(cookie->get_IsHttpOnly(&isHttpOnly));
    COREWEBVIEW2_COOKIE_SAME_SITE_KIND same_site;
    std::wstring same_site_as_string;
    CHECK_FAILURE(cookie->get_SameSite(&same_site));
    switch (same_site)
    {
    case COREWEBVIEW2_COOKIE_SAME_SITE_KIND_NONE:
        same_site_as_string = L"None";
        break;
    case COREWEBVIEW2_COOKIE_SAME_SITE_KIND_LAX:
        same_site_as_string = L"Lax";
        break;
    case COREWEBVIEW2_COOKIE_SAME_SITE_KIND_STRICT:
        same_site_as_string = L"Strict";
        break;
    }
    BOOL isSecure = FALSE;
    CHECK_FAILURE(cookie->get_IsSecure(&isSecure));
    BOOL isSession = FALSE;
    CHECK_FAILURE(cookie->get_IsSession(&isSession));

    std::wstring result = L"{";
    result += L"\"Name\": " + EncodeQuote(name.get()) + L", " + L"\"Value\": " +
              EncodeQuote(value.get()) + L", " + L"\"Domain\": " + EncodeQuote(domain.get()) +
              L", " + L"\"Path\": " + EncodeQuote(path.get()) + L", " + L"\"HttpOnly\": " +
              BoolToString(isHttpOnly) + L", " + L"\"Secure\": " + BoolToString(isSecure) + L", " +
              L"\"SameSite\": " + EncodeQuote(same_site_as_string) + L", " + L"\"Expires\": ";
    if (!!isSession)
    {
        result += L"This is a session cookie.";
    }
    else
    {
        result += std::to_wstring(expires);
    }

    return result + L"\"}";
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Domain

The domain for which the cookie is valid.

> public HRESULT [get_Domain](#get_domain)(LPWSTR * domain)

The default is the host that this cookie has been received from. Note that, for instance, ".bing.com", "bing.com", and "www.bing.com" are considered different domains.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Expires

The expiration date and time for the cookie as the number of seconds since the UNIX epoch.

> public HRESULT [get_Expires](#get_expires)(double * expires)

The default is -1.0, which means cookies are session cookies by default.

#### get_IsHttpOnly

Whether this cookie is http-only.

> public HRESULT [get_IsHttpOnly](#get_ishttponly)(BOOL * isHttpOnly)

True if a page script or other active content cannot access this cookie. The default is false.

#### get_IsSecure

The security level of this cookie.

> public HRESULT [get_IsSecure](#get_issecure)(BOOL * isSecure)

True if the client is only to return the cookie in subsequent requests if those requests use HTTPS. The default is false. Note that cookie that requests COREWEBVIEW2_COOKIE_SAME_SITE_KIND_NONE but is not marked Secure will be rejected.

#### get_IsSession

Whether this is a session cookie. The default is false.

> public HRESULT [get_IsSession](#get_issession)(BOOL * isSession)

#### get_Name

Cookie name.

> public HRESULT [get_Name](#get_name)(LPWSTR * name)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Path

The path for which the cookie is valid.

> public HRESULT [get_Path](#get_path)(LPWSTR * path)

The default is "/", which means this cookie will be sent to all pages on the Domain.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_SameSite

SameSite status of the cookie which represents the enforcement mode of the cookie.

> public HRESULT [get_SameSite](#get_samesite)(COREWEBVIEW2_COOKIE_SAME_SITE_KIND * sameSite)

The default is COREWEBVIEW2_COOKIE_SAME_SITE_KIND_LAX.

#### get_Value

Cookie value.

> public HRESULT [get_Value](#get_value)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_Expires

Set the Expires property.

> public HRESULT [put_Expires](#put_expires)(double expires)

Cookies are session cookies and will not be persistent if Expires is set to -1.0. NaN, infinity, and any negative value set other than -1.0 is disallowed.

#### put_IsHttpOnly

Set the IsHttpOnly property.

> public HRESULT [put_IsHttpOnly](#put_ishttponly)(BOOL isHttpOnly)

#### put_IsSecure

Set the IsSecure property.

> public HRESULT [put_IsSecure](#put_issecure)(BOOL isSecure)

#### put_SameSite

Set the SameSite property.

> public HRESULT [put_SameSite](#put_samesite)(COREWEBVIEW2_COOKIE_SAME_SITE_KIND sameSite)

#### put_Value

Set the cookie value property.

> public HRESULT [put_Value](#put_value)(LPCWSTR value)

