---
description: This is an interface for the StatusCode property of ICoreWebView2NavigationCompletedEventArgs.
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventArgs2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationCompletedEventArgs2
---

# interface ICoreWebView2NavigationCompletedEventArgs2

```
interface ICoreWebView2NavigationCompletedEventArgs2
  : public ICoreWebView2NavigationCompletedEventArgs
```

This is an interface for the StatusCode property of ICoreWebView2NavigationCompletedEventArgs.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HttpStatusCode](#get_httpstatuscode) | The HTTP status code of the navigation if it involved an HTTP request.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_HttpStatusCode

The HTTP status code of the navigation if it involved an HTTP request.

> public HRESULT [get_HttpStatusCode](#get_httpstatuscode)(int * http_status_code)

For instance, this will usually be 200 if the request was successful, 404 if a page was not found, etc. See https://developer.mozilla.org/docs/Web/HTTP/Status for a list of common status codes.

The `HttpStatusCode` property will be 0 in the following cases:

* The navigation did not involve an HTTP request. For instance, if it was a navigation to a file:// URL, or if it was a same-document navigation.

* The navigation failed before a response was received. For instance, if the hostname was not found, or if there was a network error.

In those cases, you can get more information from the `IsSuccess` and `WebErrorStatus` properties.

If the navigation receives a successful HTTP response, but the navigated page calls `window.stop()` before it finishes loading, then `HttpStatusCode` may contain a success code like 200, but `IsSuccess` will be FALSE and `WebErrorStatus` will be `COREWEBVIEW2_WEB_ERROR_STATUS_CONNECTION_ABORTED`.

Since WebView2 handles HTTP continuations and redirects automatically, it is unlikely for `HttpStatusCode` to ever be in the 1xx or 3xx ranges.

