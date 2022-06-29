---
description: Creates, adds or updates, gets, or or view the cookies.
title: WebView2 Win32 C++ ICoreWebView2CookieManager
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CookieManager
---

# interface ICoreWebView2CookieManager

```
interface ICoreWebView2CookieManager
  : public IUnknown
```

Creates, adds or updates, gets, or or view the cookies.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AddOrUpdateCookie](#addorupdatecookie) | Adds or updates a cookie with the given cookie data; may overwrite cookies with matching name, domain, and path if they exist.
[CopyCookie](#copycookie) | Creates a cookie whose params matches those of the specified cookie.
[CreateCookie](#createcookie) | Create a cookie object with a specified name, value, domain, and path.
[DeleteAllCookies](#deleteallcookies) | Deletes all cookies under the same profile.
[DeleteCookie](#deletecookie) | Deletes a cookie whose name and domain/path pair match those of the specified cookie.
[DeleteCookies](#deletecookies) | Deletes cookies with matching name and uri.
[DeleteCookiesWithDomainAndPath](#deletecookieswithdomainandpath) | Deletes cookies with matching name and domain/path pair.
[GetCookies](#getcookies) | Gets a list of cookies matching the specific URI.

The changes would apply to the context of the user profile. That is, other WebViews under the same user profile could be affected.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### AddOrUpdateCookie

Adds or updates a cookie with the given cookie data; may overwrite cookies with matching name, domain, and path if they exist.

> public HRESULT [AddOrUpdateCookie](#addorupdatecookie)([ICoreWebView2Cookie](icorewebview2cookie.md) * cookie)

This method will fail if the domain of the given cookie is not specified. 
```cpp
                    wil::com_ptr<ICoreWebView2Cookie> cookie;
                    CHECK_FAILURE(m_cookieManager->CreateCookie(
                        L"CookieName", L"CookieValue", L".bing.com", L"/", &cookie));
                    CHECK_FAILURE(m_cookieManager->AddOrUpdateCookie(cookie.get()));
```

#### CopyCookie

Creates a cookie whose params matches those of the specified cookie.

> public HRESULT [CopyCookie](#copycookie)([ICoreWebView2Cookie](icorewebview2cookie.md) * cookieParam, [ICoreWebView2Cookie](icorewebview2cookie.md) ** cookie)

#### CreateCookie

Create a cookie object with a specified name, value, domain, and path.

> public HRESULT [CreateCookie](#createcookie)(LPCWSTR name, LPCWSTR value, LPCWSTR domain, LPCWSTR path, [ICoreWebView2Cookie](icorewebview2cookie.md) ** cookie)

One can set other optional properties after cookie creation. This only creates a cookie object and it is not added to the cookie manager until you call AddOrUpdateCookie. Leading or trailing whitespace(s), empty string, and special characters are not allowed for name. See [ICoreWebView2Cookie](icorewebview2cookie.md) for more details.

#### DeleteAllCookies

Deletes all cookies under the same profile.

> public HRESULT [DeleteAllCookies](#deleteallcookies)()

This could affect other WebViews under the same user profile.

#### DeleteCookie

Deletes a cookie whose name and domain/path pair match those of the specified cookie.

> public HRESULT [DeleteCookie](#deletecookie)([ICoreWebView2Cookie](icorewebview2cookie.md) * cookie)

#### DeleteCookies

Deletes cookies with matching name and uri.

> public HRESULT [DeleteCookies](#deletecookies)(LPCWSTR name, LPCWSTR uri)

Cookie name is required. All cookies with the given name where domain and path match provided URI are deleted.

#### DeleteCookiesWithDomainAndPath

Deletes cookies with matching name and domain/path pair.

> public HRESULT [DeleteCookiesWithDomainAndPath](#deletecookieswithdomainandpath)(LPCWSTR name, LPCWSTR domain, LPCWSTR path)

Cookie name is required. If domain is specified, deletes only cookies with the exact domain. If path is specified, deletes only cookies with the exact path.

#### GetCookies

Gets a list of cookies matching the specific URI.

> public HRESULT [GetCookies](#getcookies)(LPCWSTR uri, [ICoreWebView2GetCookiesCompletedHandler](icorewebview2getcookiescompletedhandler.md) * handler)

If uri is empty string or null, all cookies under the same profile are returned. You can modify the cookie objects by calling [ICoreWebView2CookieManager::AddOrUpdateCookie](#addorupdatecookie), and the changes will be applied to the webview. 
```cpp
    if (m_cookieManager)
    {
        CHECK_FAILURE(m_cookieManager->GetCookies(
            uri.c_str(),
            Callback<ICoreWebView2GetCookiesCompletedHandler>(
                [this, uri](HRESULT error_code, ICoreWebView2CookieList* list) -> HRESULT {
                    CHECK_FAILURE(error_code);

                    std::wstring result;
                    UINT cookie_list_size;
                    CHECK_FAILURE(list->get_Count(&cookie_list_size));

                    if (cookie_list_size == 0)
                    {
                        result += L"No cookies found.";
                    }
                    else
                    {
                        result += std::to_wstring(cookie_list_size) + L" cookie(s) found";
                        if (!uri.empty())
                        {
                            result += L" on " + uri;
                        }
                        result += L"\n\n[";
                        for (UINT i = 0; i < cookie_list_size; ++i)
                        {
                            wil::com_ptr<ICoreWebView2Cookie> cookie;
                            CHECK_FAILURE(list->GetValueAtIndex(i, &cookie));

                            if (cookie.get())
                            {
                                result += CookieToString(cookie.get());
                                if (i != cookie_list_size - 1)
                                {
                                    result += L",\n";
                                }
                            }
                        }
                        result += L"]";
                    }
                    m_appWindow->AsyncMessageBox(std::move(result), L"GetCookies Result");
                    return S_OK;
                })
                .Get()));
    }
```

