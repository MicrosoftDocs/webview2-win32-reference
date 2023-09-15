---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponseView
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponseView
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebResourceResponseView
- ICoreWebView2WebResourceResponseView.get_Headers
- ICoreWebView2WebResourceResponseView.get_ReasonPhrase
- ICoreWebView2WebResourceResponseView.get_StatusCode
- ICoreWebView2WebResourceResponseView.GetContent
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebResourceResponseView

```
interface ICoreWebView2WebResourceResponseView
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Headers](#get_headers) | Gets the `Headers` property.
[get_ReasonPhrase](#get_reasonphrase) | Gets the `ReasonPhrase` property.
[get_StatusCode](#get_statuscode) | Gets the `StatusCode` property.
[GetContent](#getcontent) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Headers

Gets the `Headers` property.

> public HRESULT [get_Headers](#get_headers)([ICoreWebView2HttpResponseHeaders](icorewebview2httpresponseheaders.md) ** value)

#### get_ReasonPhrase

Gets the `ReasonPhrase` property.

> public HRESULT [get_ReasonPhrase](#get_reasonphrase)(LPWSTR * value)

#### get_StatusCode

Gets the `StatusCode` property.

> public HRESULT [get_StatusCode](#get_statuscode)(INT32 * value)

#### GetContent

> public HRESULT [GetContent](#getcontent)([ICoreWebView2WebResourceResponseViewGetContentCompletedHandler](icorewebview2webresourceresponseviewgetcontentcompletedhandler.md) * handler)

