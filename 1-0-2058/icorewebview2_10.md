---
description: 
title: WebView2 Win32 C++ ICoreWebView2_10
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_10
topic_type: 
- APIRef
api_name:
- ICoreWebView2_10
- ICoreWebView2_10.add_BasicAuthenticationRequested
- ICoreWebView2_10.remove_BasicAuthenticationRequested
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_10

```
interface ICoreWebView2_10
  : public ICoreWebView2_9
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BasicAuthenticationRequested](#add_basicauthenticationrequested) | Adds an event handler for the `BasicAuthenticationRequested` event.
[remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested) | Removes an event handler previously added with `add_BasicAuthenticationRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_BasicAuthenticationRequested

Adds an event handler for the `BasicAuthenticationRequested` event.

> public HRESULT [add_BasicAuthenticationRequested](#add_basicauthenticationrequested)([ICoreWebView2BasicAuthenticationRequestedEventHandler](icorewebview2basicauthenticationrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_BasicAuthenticationRequested

Removes an event handler previously added with `add_BasicAuthenticationRequested`.

> public HRESULT [remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested)(EventRegistrationToken token)

