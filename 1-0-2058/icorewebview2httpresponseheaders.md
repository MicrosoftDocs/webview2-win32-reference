---
description: 
title: WebView2 Win32 C++ ICoreWebView2HttpResponseHeaders
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2HttpResponseHeaders
topic_type: 
- APIRef
api_name:
- ICoreWebView2HttpResponseHeaders
- ICoreWebView2HttpResponseHeaders.AppendHeader
- ICoreWebView2HttpResponseHeaders.Contains
- ICoreWebView2HttpResponseHeaders.GetHeader
- ICoreWebView2HttpResponseHeaders.GetHeaders
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2HttpResponseHeaders

```
interface ICoreWebView2HttpResponseHeaders
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AppendHeader](#appendheader) | 
[Contains](#contains) | 
[GetHeader](#getheader) | 
[GetHeaders](#getheaders) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### AppendHeader

> public HRESULT [AppendHeader](#appendheader)(LPCWSTR name, LPCWSTR value)

#### Contains

> public HRESULT [Contains](#contains)(LPCWSTR name, BOOL * value)

#### GetHeader

> public HRESULT [GetHeader](#getheader)(LPCWSTR name, LPWSTR * value)

#### GetHeaders

> public HRESULT [GetHeaders](#getheaders)(LPCWSTR name, ICoreWebView2HttpHeadersCollectionIterator ** value)

