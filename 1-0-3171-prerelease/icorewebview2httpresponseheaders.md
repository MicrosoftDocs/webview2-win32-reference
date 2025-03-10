---
description: HTTP response headers.
title: WebView2 Win32 C++ ICoreWebView2HttpResponseHeaders
ms.date: 03/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2HttpResponseHeaders
topic_type: 
- APIRef
api_name:
- ICoreWebView2HttpResponseHeaders
- ICoreWebView2HttpResponseHeaders.AppendHeader
- ICoreWebView2HttpResponseHeaders.Contains
- ICoreWebView2HttpResponseHeaders.GetHeader
- ICoreWebView2HttpResponseHeaders.GetHeaders
- ICoreWebView2HttpResponseHeaders.GetIterator
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

HTTP response headers.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AppendHeader](#appendheader) | Appends header line with name and value.
[Contains](#contains) | Verifies that the headers contain entries that match the header name.
[GetHeader](#getheader) | Gets the first header value in the collection matching the name.
[GetHeaders](#getheaders) | Gets the header values matching the name.
[GetIterator](#getiterator) | Gets an iterator over the collection of entire response headers.

Used to construct a `WebResourceResponse` for the `WebResourceRequested` event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### AppendHeader

Appends header line with name and value.

> public HRESULT [AppendHeader](#appendheader)(LPCWSTR name, LPCWSTR value)

#### Contains

Verifies that the headers contain entries that match the header name.

> public HRESULT [Contains](#contains)(LPCWSTR name, BOOL * value)

#### GetHeader

Gets the first header value in the collection matching the name.

> public HRESULT [GetHeader](#getheader)(LPCWSTR name, LPWSTR * value)

#### GetHeaders

Gets the header values matching the name.

> public HRESULT [GetHeaders](#getheaders)(LPCWSTR name, [ICoreWebView2HttpHeadersCollectionIterator](icorewebview2httpheaderscollectioniterator.md#icorewebview2httpheaderscollectioniterator) ** value)

#### GetIterator

Gets an iterator over the collection of entire response headers.

> public HRESULT [GetIterator](#getiterator)([ICoreWebView2HttpHeadersCollectionIterator](icorewebview2httpheaderscollectioniterator.md#icorewebview2httpheaderscollectioniterator) ** value)

