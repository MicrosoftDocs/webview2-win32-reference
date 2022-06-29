---
description: Event args for the `NavigationStarting` event.
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventArgs
---

# interface ICoreWebView2NavigationStartingEventArgs

```
interface ICoreWebView2NavigationStartingEventArgs
  : public IUnknown
```

Event args for the `NavigationStarting` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | The host may set this flag to cancel the navigation.
[get_IsRedirected](#get_isredirected) | `TRUE` when the navigation is redirected.
[get_IsUserInitiated](#get_isuserinitiated) | `TRUE` when the navigation was initiated through a user gesture as opposed to programmatic navigation by page script.
[get_NavigationId](#get_navigationid) | The ID of the navigation.
[get_RequestHeaders](#get_requestheaders) | The HTTP request headers for the navigation.
[get_Uri](#get_uri) | The uri of the requested navigation.
[put_Cancel](#put_cancel) | Sets the `Cancel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Cancel

The host may set this flag to cancel the navigation.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * cancel)

If set, the navigation is not longer present and the content of the current page is intact. For performance reasons, `GET` HTTP requests may happen, while the host is responding. You may set cookies and use part of a request for the navigation. Cancellation for navigation to `about:blank` or frame navigation to `srcdoc` is not supported. Such attempts are ignored. A cancelled navigation will fire a `NavigationCompleted` event with a `WebErrorStatus` of `COREWEBVIEW2_WEB_ERROR_STATUS_OPERATION_CANCELED`.

#### get_IsRedirected

`TRUE` when the navigation is redirected.

> public HRESULT [get_IsRedirected](#get_isredirected)(BOOL * isRedirected)

#### get_IsUserInitiated

`TRUE` when the navigation was initiated through a user gesture as opposed to programmatic navigation by page script.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * isUserInitiated)

Navigations initiated via WebView2 APIs are considered as user initiated.

#### get_NavigationId

The ID of the navigation.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * navigationId)

#### get_RequestHeaders

The HTTP request headers for the navigation.

> public HRESULT [get_RequestHeaders](#get_requestheaders)(ICoreWebView2HttpRequestHeaders ** requestHeaders)

> [!NOTE]
> You are not able to modify the HTTP request headers in a `NavigationStarting` event.

#### get_Uri

The uri of the requested navigation.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL cancel)

