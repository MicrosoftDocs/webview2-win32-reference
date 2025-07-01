---
description: Event args for the WebResourceResponseReceived event.
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponseReceivedEventArgs
ms.date: 05/26/2025
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2WebResourceResponseReceivedEventArgs
  : public IUnknown
```

Event args for the WebResourceResponseReceived event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Request](#get_request) | The request object for the web resource, as committed.
[get_Response](#get_response) | View of the response object received for the web resource.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_Request

The request object for the web resource, as committed.

> public HRESULT [get_Request](#get_request)([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md#icorewebview2webresourcerequest) ** value)

This includes headers added by the network stack that were not be included during the associated WebResourceRequested event, such as Authentication headers. Modifications to this object have no effect on how the request is processed as it has already been sent.

#### get_Response

View of the response object received for the web resource.

> public HRESULT [get_Response](#get_response)([ICoreWebView2WebResourceResponseView](icorewebview2webresourceresponseview.md#icorewebview2webresourceresponseview) ** value)

