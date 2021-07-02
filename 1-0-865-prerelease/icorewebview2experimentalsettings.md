---
description: The ICoreWebView2Settings Experimental interface to manage the User Agent.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings
---

# interface ICoreWebView2ExperimentalSettings

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings
  : public IUnknown
```

The [ICoreWebView2Settings](icorewebview2settings.md) Experimental interface to manage the User Agent.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserAgent](#get_useragent) | `UserAgent`.
[put_UserAgent](#put_useragent) | Sets the `UserAgent` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.790

## Members

#### get_UserAgent

`UserAgent`.

> public HRESULT [get_UserAgent](#get_useragent)(LPWSTR * userAgent)

Returns the User Agent. The default value is the default User Agent of the Edge browser. 
```cpp
                if (m_settings2)
                {
                    static const PCWSTR url_compare_example = L"fourthcoffee.com";
                    wil::unique_bstr domain = GetDomainOfUri(uri.get());
                    const wchar_t* domains = domain.get();

                    if (wcscmp(url_compare_example, domains) == 0)
                    {
                        SetUserAgent(L"example_navigation_ua");
                    }
                }
```

#### put_UserAgent

Sets the `UserAgent` property.

> public HRESULT [put_UserAgent](#put_useragent)(LPCWSTR userAgent)

This property may be overridden if the User-Agent header is set in a request. If the parameter is empty the User Agent will not be updated and the current User Agent will remain.

