---
description: 
title: WebView2 Win32 C++ ICoreWebView2CookieManager
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CookieManager
topic_type: 
- APIRef
api_name:
- ICoreWebView2CookieManager
- ICoreWebView2CookieManager.AddOrUpdateCookie
- ICoreWebView2CookieManager.CopyCookie
- ICoreWebView2CookieManager.CreateCookie
- ICoreWebView2CookieManager.DeleteAllCookies
- ICoreWebView2CookieManager.DeleteCookie
- ICoreWebView2CookieManager.DeleteCookies
- ICoreWebView2CookieManager.DeleteCookiesWithDomainAndPath
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CookieManager

```
interface ICoreWebView2CookieManager
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AddOrUpdateCookie](#addorupdatecookie) | 
[CopyCookie](#copycookie) | 
[CreateCookie](#createcookie) | 
[DeleteAllCookies](#deleteallcookies) | 
[DeleteCookie](#deletecookie) | 
[DeleteCookies](#deletecookies) | 
[DeleteCookiesWithDomainAndPath](#deletecookieswithdomainandpath) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### AddOrUpdateCookie

> public HRESULT [AddOrUpdateCookie](#addorupdatecookie)([ICoreWebView2Cookie](icorewebview2cookie.md) * cookie)

#### CopyCookie

> public HRESULT [CopyCookie](#copycookie)([ICoreWebView2Cookie](icorewebview2cookie.md) * cookieParam, [ICoreWebView2Cookie](icorewebview2cookie.md) ** value)

#### CreateCookie

> public HRESULT [CreateCookie](#createcookie)(LPCWSTR name, LPCWSTR value, LPCWSTR Domain, LPCWSTR Path, [ICoreWebView2Cookie](icorewebview2cookie.md) ** value)

#### DeleteAllCookies

> public HRESULT [DeleteAllCookies](#deleteallcookies)()

#### DeleteCookie

> public HRESULT [DeleteCookie](#deletecookie)([ICoreWebView2Cookie](icorewebview2cookie.md) * cookie)

#### DeleteCookies

> public HRESULT [DeleteCookies](#deletecookies)(LPCWSTR name, LPCWSTR uri)

#### DeleteCookiesWithDomainAndPath

> public HRESULT [DeleteCookiesWithDomainAndPath](#deletecookieswithdomainandpath)(LPCWSTR name, LPCWSTR Domain, LPCWSTR Path)

