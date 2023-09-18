---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebResourceRequest
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceRequest
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebResourceRequest
- ICoreWebView2WebResourceRequest.get_Content
- ICoreWebView2WebResourceRequest.get_Headers
- ICoreWebView2WebResourceRequest.get_Method
- ICoreWebView2WebResourceRequest.get_Uri
- ICoreWebView2WebResourceRequest.put_Content
- ICoreWebView2WebResourceRequest.put_Method
- ICoreWebView2WebResourceRequest.put_Uri
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebResourceRequest

```
interface ICoreWebView2WebResourceRequest
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Content](#get_content) | Gets the `Content` property.
[get_Headers](#get_headers) | Gets the `Headers` property.
[get_Method](#get_method) | Gets the `Method` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[put_Content](#put_content) | Sets the `Content` property.
[put_Method](#put_method) | Sets the `Method` property.
[put_Uri](#put_uri) | Sets the `Uri` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Content

Gets the `Content` property.

> public HRESULT [get_Content](#get_content)(IStream ** value)

#### get_Headers

Gets the `Headers` property.

> public HRESULT [get_Headers](#get_headers)([ICoreWebView2HttpRequestHeaders](icorewebview2httprequestheaders.md) ** value)

#### get_Method

Gets the `Method` property.

> public HRESULT [get_Method](#get_method)(LPWSTR * value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### put_Content

Sets the `Content` property.

> public HRESULT [put_Content](#put_content)(IStream * value)

#### put_Method

Sets the `Method` property.

> public HRESULT [put_Method](#put_method)(LPCWSTR value)

#### put_Uri

Sets the `Uri` property.

> public HRESULT [put_Uri](#put_uri)(LPCWSTR value)

