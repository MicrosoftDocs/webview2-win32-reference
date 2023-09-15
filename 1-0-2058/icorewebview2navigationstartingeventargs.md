---
description: 
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationStartingEventArgs
- ICoreWebView2NavigationStartingEventArgs.get_Cancel
- ICoreWebView2NavigationStartingEventArgs.get_IsRedirected
- ICoreWebView2NavigationStartingEventArgs.get_IsUserInitiated
- ICoreWebView2NavigationStartingEventArgs.get_NavigationId
- ICoreWebView2NavigationStartingEventArgs.get_RequestHeaders
- ICoreWebView2NavigationStartingEventArgs.get_Uri
- ICoreWebView2NavigationStartingEventArgs.put_Cancel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NavigationStartingEventArgs

```
interface ICoreWebView2NavigationStartingEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_IsRedirected](#get_isredirected) | Gets the `IsRedirected` property.
[get_IsUserInitiated](#get_isuserinitiated) | Gets the `IsUserInitiated` property.
[get_NavigationId](#get_navigationid) | Gets the `NavigationId` property.
[get_RequestHeaders](#get_requestheaders) | Gets the `RequestHeaders` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[put_Cancel](#put_cancel) | Sets the `Cancel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Cancel

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_IsRedirected

Gets the `IsRedirected` property.

> public HRESULT [get_IsRedirected](#get_isredirected)(BOOL * value)

#### get_IsUserInitiated

Gets the `IsUserInitiated` property.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * value)

#### get_NavigationId

Gets the `NavigationId` property.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * value)

#### get_RequestHeaders

Gets the `RequestHeaders` property.

> public HRESULT [get_RequestHeaders](#get_requestheaders)([ICoreWebView2HttpRequestHeaders](icorewebview2httprequestheaders.md) ** value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

