---
description: HTTP request headers.
title: WebView2 Win32 C++ ICoreWebView2HttpRequestHeaders
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2HttpRequestHeaders
---

# interface ICoreWebView2HttpRequestHeaders

```
interface ICoreWebView2HttpRequestHeaders
  : public IUnknown
```

HTTP request headers.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Contains](#contains) | Verifies that the headers contain an entry that matches the header name.
[GetHeader](#getheader) | Gets the header value matching the name.
[GetHeaders](#getheaders) | Gets the header value matching the name using an iterator.
[GetIterator](#getiterator) | Gets an iterator over the collection of request headers.
[RemoveHeader](#removeheader) | Removes header that matches the name.
[SetHeader](#setheader) | Adds or updates header that matches the name.

Used to inspect the HTTP request on `WebResourceRequested` event and `NavigationStarting` event.

> [!NOTE]
> It is possible to modify the HTTP request from a `WebResourceRequested` event, but not from a `NavigationStarting` event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Contains

Verifies that the headers contain an entry that matches the header name.

> public HRESULT [Contains](#contains)(LPCWSTR name, BOOL * contains)

#### GetHeader

Gets the header value matching the name.

> public HRESULT [GetHeader](#getheader)(LPCWSTR name, LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetHeaders

Gets the header value matching the name using an iterator.

> public HRESULT [GetHeaders](#getheaders)(LPCWSTR name, ICoreWebView2HttpHeadersCollectionIterator ** iterator)

#### GetIterator

Gets an iterator over the collection of request headers.

> public HRESULT [GetIterator](#getiterator)(ICoreWebView2HttpHeadersCollectionIterator ** iterator)

#### RemoveHeader

Removes header that matches the name.

> public HRESULT [RemoveHeader](#removeheader)(LPCWSTR name)

#### SetHeader

Adds or updates header that matches the name.

> public HRESULT [SetHeader](#setheader)(LPCWSTR name, LPCWSTR value)

