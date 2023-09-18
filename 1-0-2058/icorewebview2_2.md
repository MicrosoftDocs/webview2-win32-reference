---
description: 
title: WebView2 Win32 C++ ICoreWebView2_2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_2
topic_type: 
- APIRef
api_name:
- ICoreWebView2_2
- ICoreWebView2_2.add_DOMContentLoaded
- ICoreWebView2_2.add_WebResourceResponseReceived
- ICoreWebView2_2.get_CookieManager
- ICoreWebView2_2.get_Environment
- ICoreWebView2_2.NavigateWithWebResourceRequest
- ICoreWebView2_2.remove_DOMContentLoaded
- ICoreWebView2_2.remove_WebResourceResponseReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_2

```
interface ICoreWebView2_2
  : public ICoreWebView2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DOMContentLoaded](#add_domcontentloaded) | Adds an event handler for the `DOMContentLoaded` event.
[add_WebResourceResponseReceived](#add_webresourceresponsereceived) | Adds an event handler for the `WebResourceResponseReceived` event.
[get_CookieManager](#get_cookiemanager) | Gets the `CookieManager` property.
[get_Environment](#get_environment) | Gets the `Environment` property.
[NavigateWithWebResourceRequest](#navigatewithwebresourcerequest) | 
[remove_DOMContentLoaded](#remove_domcontentloaded) | Removes an event handler previously added with `add_DOMContentLoaded`.
[remove_WebResourceResponseReceived](#remove_webresourceresponsereceived) | Removes an event handler previously added with `add_WebResourceResponseReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### add_DOMContentLoaded

Adds an event handler for the `DOMContentLoaded` event.

> public HRESULT [add_DOMContentLoaded](#add_domcontentloaded)([ICoreWebView2DOMContentLoadedEventHandler](icorewebview2domcontentloadedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### add_WebResourceResponseReceived

Adds an event handler for the `WebResourceResponseReceived` event.

> public HRESULT [add_WebResourceResponseReceived](#add_webresourceresponsereceived)([ICoreWebView2WebResourceResponseReceivedEventHandler](icorewebview2webresourceresponsereceivedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_CookieManager

Gets the `CookieManager` property.

> public HRESULT [get_CookieManager](#get_cookiemanager)([ICoreWebView2CookieManager](icorewebview2cookiemanager.md) ** value)

#### get_Environment

Gets the `Environment` property.

> public HRESULT [get_Environment](#get_environment)([ICoreWebView2Environment](icorewebview2environment.md) ** value)

#### NavigateWithWebResourceRequest

> public HRESULT [NavigateWithWebResourceRequest](#navigatewithwebresourcerequest)([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) * Request)

#### remove_DOMContentLoaded

Removes an event handler previously added with `add_DOMContentLoaded`.

> public HRESULT [remove_DOMContentLoaded](#remove_domcontentloaded)(EventRegistrationToken token)

#### remove_WebResourceResponseReceived

Removes an event handler previously added with `add_WebResourceResponseReceived`.

> public HRESULT [remove_WebResourceResponseReceived](#remove_webresourceresponsereceived)(EventRegistrationToken token)

