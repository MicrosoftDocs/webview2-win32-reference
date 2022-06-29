---
description: An HTTP request used with the `WebResourceRequested` event.
title: WebView2 Win32 C++ ICoreWebView2WebResourceRequest
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceRequest
---

# interface ICoreWebView2WebResourceRequest

```
interface ICoreWebView2WebResourceRequest
  : public IUnknown
```

An HTTP request used with the `WebResourceRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Content](#get_content) | The HTTP request message body as stream.
[get_Headers](#get_headers) | The mutable HTTP request headers.
[get_Method](#get_method) | The HTTP request method.
[get_Uri](#get_uri) | The request URI.
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

The HTTP request message body as stream.

> public HRESULT [get_Content](#get_content)(IStream ** content)

POST data should be here. If a stream is set, which overrides the message body, the stream must have all the content data available by the time the `WebResourceRequested` event deferral of this response is completed. Stream should be agile or be created from a background STA to prevent performance impact to the UI thread. `Null` means no content data. `IStream` semantics apply (return `S_OK` to `Read` runs until all data is exhausted).

#### get_Headers

The mutable HTTP request headers.

> public HRESULT [get_Headers](#get_headers)(ICoreWebView2HttpRequestHeaders ** headers)

#### get_Method

The HTTP request method.

> public HRESULT [get_Method](#get_method)(LPWSTR * method)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Uri

The request URI.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_Content

Sets the `Content` property.

> public HRESULT [put_Content](#put_content)(IStream * content)

#### put_Method

Sets the `Method` property.

> public HRESULT [put_Method](#put_method)(LPCWSTR method)

#### put_Uri

Sets the `Uri` property.

> public HRESULT [put_Uri](#put_uri)(LPCWSTR uri)

