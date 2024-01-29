---
description: A continuation of the ICoreWebView2Settings interface that manages the user agent.
title: WebView2 Win32 C++ ICoreWebView2Settings2
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings2
---

# interface ICoreWebView2Settings2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Settings2
  : public ICoreWebView2Settings
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md) interface that manages the user agent.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserAgent](#get_useragent) | Returns the User Agent.
[put_UserAgent](#put_useragent) | Sets the `UserAgent` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_UserAgent

Returns the User Agent.

> public HRESULT [get_UserAgent](#get_useragent)(LPWSTR * userAgent)

The default value is the default User Agent of the Microsoft Edge browser.

#### put_UserAgent

Sets the `UserAgent` property.

> public HRESULT [put_UserAgent](#put_useragent)(LPCWSTR userAgent)

This property may be overridden if the User-Agent header is set in a request. If the parameter is empty the User Agent will not be updated and the current User Agent will remain.

