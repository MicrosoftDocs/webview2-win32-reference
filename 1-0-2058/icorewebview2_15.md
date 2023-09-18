---
description: 
title: WebView2 Win32 C++ ICoreWebView2_15
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_15
topic_type: 
- APIRef
api_name:
- ICoreWebView2_15
- ICoreWebView2_15.add_FaviconChanged
- ICoreWebView2_15.get_FaviconUri
- ICoreWebView2_15.GetFavicon
- ICoreWebView2_15.remove_FaviconChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_15

```
interface ICoreWebView2_15
  : public ICoreWebView2_14
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_FaviconChanged](#add_faviconchanged) | Adds an event handler for the `FaviconChanged` event.
[get_FaviconUri](#get_faviconuri) | Gets the `FaviconUri` property.
[GetFavicon](#getfavicon) | 
[remove_FaviconChanged](#remove_faviconchanged) | Removes an event handler previously added with `add_FaviconChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1293.44
WebView2 Win32 Prerelease |    1.0.1305

## Members

#### add_FaviconChanged

Adds an event handler for the `FaviconChanged` event.

> public HRESULT [add_FaviconChanged](#add_faviconchanged)([ICoreWebView2FaviconChangedEventHandler](icorewebview2faviconchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_FaviconUri

Gets the `FaviconUri` property.

> public HRESULT [get_FaviconUri](#get_faviconuri)(LPWSTR * value)

#### GetFavicon

> public HRESULT [GetFavicon](#getfavicon)(COREWEBVIEW2_FAVICON_IMAGE_FORMAT format, [ICoreWebView2GetFaviconCompletedHandler](icorewebview2getfaviconcompletedhandler.md) * handler)

#### remove_FaviconChanged

Removes an event handler previously added with `add_FaviconChanged`.

> public HRESULT [remove_FaviconChanged](#remove_faviconchanged)(EventRegistrationToken token)

