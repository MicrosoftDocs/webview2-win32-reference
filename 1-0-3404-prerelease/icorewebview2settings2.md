---
description: A continuation of the ICoreWebView2Settings interface that manages the user agent.
title: WebView2 Win32 C++ ICoreWebView2Settings2
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings2
- ICoreWebView2Settings2.get_UserAgent
- ICoreWebView2Settings2.put_UserAgent
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings2

```
interface ICoreWebView2Settings2
  : public ICoreWebView2Settings
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface that manages the user agent.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserAgent](#get_useragent) | Gets the `UserAgent` property.
[put_UserAgent](#put_useragent) | This setting determines the UserAgent of WebView.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.864.35
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_UserAgent

Gets the `UserAgent` property.

> public HRESULT [get_UserAgent](#get_useragent)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_UserAgent

This setting determines the UserAgent of WebView.

> public HRESULT [put_UserAgent](#put_useragent)(LPCWSTR value)

This property may be overridden if the User-Agent header is set in a request. If the parameter is empty the User Agent will not be updated and the current User Agent will remain. Setting this property may clear User Agent Client Hints headers Sec-CH-UA-* and script values from navigator.userAgentData. Current implementation behavior is subject to change. The User Agent set will also be effective on service workers and shared workers associated with the WebView. If there are multiple WebViews associated with the same service worker or shared worker, the last User Agent set will be used.

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

