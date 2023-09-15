---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponseReceivedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponseReceivedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebResourceResponseReceivedEventArgs
- ICoreWebView2WebResourceResponseReceivedEventArgs.get_Request
- ICoreWebView2WebResourceResponseReceivedEventArgs.get_Response
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebResourceResponseReceivedEventArgs

```
interface ICoreWebView2WebResourceResponseReceivedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Request](#get_request) | Gets the `Request` property.
[get_Response](#get_response) | Gets the `Response` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Request

Gets the `Request` property.

> public HRESULT [get_Request](#get_request)([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) ** value)

#### get_Response

Gets the `Response` property.

> public HRESULT [get_Response](#get_response)([ICoreWebView2WebResourceResponseView](icorewebview2webresourceresponseview.md) ** value)

