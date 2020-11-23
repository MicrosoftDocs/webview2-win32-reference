---
description: A list of cookie objects.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCookieList
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCookieList
---

# interface ICoreWebView2ExperimentalCookieList 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCookieList
  : public IUnknown
```

A list of cookie objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of cookies contained in the ICoreWebView2ExperimentalCookieList.
[GetValueAtIndex](#getvalueatindex) | Gets the cookie object at the given index.

See [ICoreWebView2ExperimentalCookie](icorewebview2experimentalcookie.md). 
```cpp
    if (m_cookieManager)
    {
        CHECK_FAILURE(m_cookieManager->GetCookies(
            uri.c_str(),
            Callback<ICoreWebView2ExperimentalGetCookiesCompletedHandler>(
                [this, uri](HRESULT error_code, ICoreWebView2ExperimentalCookieList* list) -> HRESULT {
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
                        for (int i = 0; i < cookie_list_size; ++i)
                        {
                            wil::com_ptr<ICoreWebView2ExperimentalCookie> cookie;
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
                    MessageBox(nullptr, result.c_str(), L"GetCookies Result", MB_OK);
                    return S_OK;
                })
                .Get()));
    }
```

## Members

#### get_Count 

The number of cookies contained in the ICoreWebView2ExperimentalCookieList.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex 

Gets the cookie object at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, [ICoreWebView2ExperimentalCookie](icorewebview2experimentalcookie.md) ** cookie)

