---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebResourceRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebResourceRequestedEventArgs
- ICoreWebView2WebResourceRequestedEventArgs.get_Request
- ICoreWebView2WebResourceRequestedEventArgs.get_ResourceContext
- ICoreWebView2WebResourceRequestedEventArgs.get_Response
- ICoreWebView2WebResourceRequestedEventArgs.GetDeferral
- ICoreWebView2WebResourceRequestedEventArgs.put_Response
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebResourceRequestedEventArgs

```
interface ICoreWebView2WebResourceRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Request](#get_request) | Gets the `Request` property.
[get_ResourceContext](#get_resourcecontext) | Gets the `ResourceContext` property.
[get_Response](#get_response) | Gets the `Response` property.
[GetDeferral](#getdeferral) | 
[put_Response](#put_response) | Sets the `Response` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Request

Gets the `Request` property.

> public HRESULT [get_Request](#get_request)([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) ** value)

#### get_ResourceContext

Gets the `ResourceContext` property.

> public HRESULT [get_ResourceContext](#get_resourcecontext)(COREWEBVIEW2_WEB_RESOURCE_CONTEXT * value)

#### get_Response

Gets the `Response` property.

> public HRESULT [get_Response](#get_response)([ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) ** value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Response

Sets the `Response` property.

> public HRESULT [put_Response](#put_response)([ICoreWebView2WebResourceResponse](icorewebview2webresourceresponse.md) * value)

