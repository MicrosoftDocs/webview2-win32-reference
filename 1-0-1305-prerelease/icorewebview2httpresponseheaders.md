---
description: HTTP response headers.
title: WebView2 Win32 C++ ICoreWebView2HttpResponseHeaders
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2HttpResponseHeaders
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

> public HRESULT [Contains](#contains)(LPCWSTR name, BOOL * contains)

#### GetHeader

Gets the first header value in the collection matching the name.

> public HRESULT [GetHeader](#getheader)(LPCWSTR name, LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetHeaders

Gets the header values matching the name.

> public HRESULT [GetHeaders](#getheaders)(LPCWSTR name, ICoreWebView2HttpHeadersCollectionIterator ** iterator)

#### GetIterator

Gets an iterator over the collection of entire response headers.

> public HRESULT [GetIterator](#getiterator)(ICoreWebView2HttpHeadersCollectionIterator ** iterator)

