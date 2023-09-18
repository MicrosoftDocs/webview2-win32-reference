---
description: 
title: WebView2 Win32 C++ ICoreWebView2HttpRequestHeaders
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2HttpRequestHeaders
topic_type: 
- APIRef
api_name:
- ICoreWebView2HttpRequestHeaders
- ICoreWebView2HttpRequestHeaders.Contains
- ICoreWebView2HttpRequestHeaders.GetHeader
- ICoreWebView2HttpRequestHeaders.GetHeaders
- ICoreWebView2HttpRequestHeaders.RemoveHeader
- ICoreWebView2HttpRequestHeaders.SetHeader
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2HttpRequestHeaders

```
interface ICoreWebView2HttpRequestHeaders
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Contains](#contains) | 
[GetHeader](#getheader) | 
[GetHeaders](#getheaders) | 
[RemoveHeader](#removeheader) | 
[SetHeader](#setheader) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Contains

> public HRESULT [Contains](#contains)(LPCWSTR name, BOOL * value)

#### GetHeader

> public HRESULT [GetHeader](#getheader)(LPCWSTR name, LPWSTR * value)

#### GetHeaders

> public HRESULT [GetHeaders](#getheaders)(LPCWSTR name, ICoreWebView2HttpHeadersCollectionIterator ** value)

#### RemoveHeader

> public HRESULT [RemoveHeader](#removeheader)(LPCWSTR name)

#### SetHeader

> public HRESULT [SetHeader](#setheader)(LPCWSTR name, LPCWSTR value)

