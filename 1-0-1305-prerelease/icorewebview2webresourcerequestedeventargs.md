---
description: Event args for the `WebResourceRequested` event.
title: WebView2 Win32 C++ ICoreWebView2WebResourceRequestedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceRequestedEventArgs
---

# interface ICoreWebView2WebResourceRequestedEventArgs

```
interface ICoreWebView2WebResourceRequestedEventArgs
  : public IUnknown
```

Event args for the `WebResourceRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Request](#get_request) | The Web resource request.
[get_ResourceContext](#get_resourcecontext) | The web resource request context.
[get_Response](#get_response) | A placeholder for the web resource response object.
[GetDeferral](#getdeferral) | Obtain an ICoreWebView2Deferral object and put the event into a deferred state.
[put_Response](#put_response) | Sets the `Response` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Request

The Web resource request.

> public HRESULT [get_Request](#get_request)(ICoreWebView2WebResourceRequest ** request)

The request object may be missing some headers that are added by network stack at a later time.

#### get_ResourceContext

The web resource request context.

> public HRESULT [get_ResourceContext](#get_resourcecontext)(COREWEBVIEW2_WEB_RESOURCE_CONTEXT * context)

#### get_Response

A placeholder for the web resource response object.

> public HRESULT [get_Response](#get_response)(ICoreWebView2WebResourceResponse ** response)

If this object is set, the web resource request is completed with the specified response.

#### GetDeferral

Obtain an ICoreWebView2Deferral object and put the event into a deferred state.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use the ICoreWebView2Deferral object to complete the request at a later time.

#### put_Response

Sets the `Response` property.

> public HRESULT [put_Response](#put_response)(ICoreWebView2WebResourceResponse * response)

Create an empty web resource response object with `CreateWebResourceResponse` and then modify it to construct the response.

