---
description: A list of cookie objects.
title: WebView2 Win32 C++ ICoreWebView2CookieList
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CookieList
---

# interface ICoreWebView2CookieList

```
interface ICoreWebView2CookieList
  : public IUnknown
```

A list of cookie objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of cookies contained in the ICoreWebView2CookieList.
[GetValueAtIndex](#getvalueatindex) | Gets the cookie object at the given index.

See ICoreWebView2Cookie. 
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

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Count

The number of cookies contained in the ICoreWebView2CookieList.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the cookie object at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, [ICoreWebView2Cookie](icorewebview2cookie.md) ** cookie)

