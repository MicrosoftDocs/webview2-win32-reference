---
description: An HTTP response used with the `WebResourceRequested` event.
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponse
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponse
---

# interface ICoreWebView2WebResourceResponse

```
interface ICoreWebView2WebResourceResponse
  : public IUnknown
```

An HTTP response used with the `WebResourceRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Content](#get_content) | HTTP response content as stream.
[get_Headers](#get_headers) | Overridden HTTP response headers.
[get_ReasonPhrase](#get_reasonphrase) | The HTTP response reason phrase.
[get_StatusCode](#get_statuscode) | The HTTP response status code.
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

HTTP response content as stream.

> public HRESULT [get_Content](#get_content)(IStream ** content)

Stream must have all the content data available by the time the `WebResourceRequested` event deferral of this response is completed. Stream should be agile or be created from a background thread to prevent performance impact to the UI thread. `Null` means no content data. `IStream` semantics apply (return `S_OK` to `Read` runs until all data is exhausted).

#### get_Headers

Overridden HTTP response headers.

> public HRESULT [get_Headers](#get_headers)(ICoreWebView2HttpResponseHeaders ** headers)

#### get_ReasonPhrase

The HTTP response reason phrase.

> public HRESULT [get_ReasonPhrase](#get_reasonphrase)(LPWSTR * reasonPhrase)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_StatusCode

The HTTP response status code.

> public HRESULT [get_StatusCode](#get_statuscode)(int * statusCode)

#### put_Content

Sets the `Content` property.

> public HRESULT [put_Content](#put_content)(IStream * content)

#### put_ReasonPhrase

Sets the `ReasonPhrase` property.

> public HRESULT [put_ReasonPhrase](#put_reasonphrase)(LPCWSTR reasonPhrase)

#### put_StatusCode

Sets the `StatusCode` property.

> public HRESULT [put_StatusCode](#put_statuscode)(int statusCode)

