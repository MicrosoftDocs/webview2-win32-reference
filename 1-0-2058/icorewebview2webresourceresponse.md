---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponse
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponse
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebResourceResponse
- ICoreWebView2WebResourceResponse.get_Content
- ICoreWebView2WebResourceResponse.get_Headers
- ICoreWebView2WebResourceResponse.get_ReasonPhrase
- ICoreWebView2WebResourceResponse.get_StatusCode
- ICoreWebView2WebResourceResponse.put_Content
- ICoreWebView2WebResourceResponse.put_ReasonPhrase
- ICoreWebView2WebResourceResponse.put_StatusCode
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebResourceResponse

```
interface ICoreWebView2WebResourceResponse
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Content](#get_content) | Gets the `Content` property.
[get_Headers](#get_headers) | Gets the `Headers` property.
[get_ReasonPhrase](#get_reasonphrase) | Gets the `ReasonPhrase` property.
[get_StatusCode](#get_statuscode) | Gets the `StatusCode` property.
[put_Content](#put_content) | Sets the `Content` property.
[put_ReasonPhrase](#put_reasonphrase) | Sets the `ReasonPhrase` property.
[put_StatusCode](#put_statuscode) | Sets the `StatusCode` property.

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

> public HRESULT [get_Headers](#get_headers)([ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md) ** value)

#### get_ReasonPhrase

Gets the `ReasonPhrase` property.

> public HRESULT [get_ReasonPhrase](#get_reasonphrase)(LPWSTR * value)

#### get_StatusCode

Gets the `StatusCode` property.

> public HRESULT [get_StatusCode](#get_statuscode)(INT32 * value)

#### put_Content

Sets the `Content` property.

> public HRESULT [put_Content](#put_content)(IStream * value)

#### put_ReasonPhrase

Sets the `ReasonPhrase` property.

> public HRESULT [put_ReasonPhrase](#put_reasonphrase)(LPCWSTR value)

#### put_StatusCode

Sets the `StatusCode` property.

> public HRESULT [put_StatusCode](#put_statuscode)(INT32 value)

