---
description: 
title: WebView2 Win32 C++ ICoreWebView2BasicAuthenticationRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BasicAuthenticationRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2BasicAuthenticationRequestedEventArgs
- ICoreWebView2BasicAuthenticationRequestedEventArgs.get_Cancel
- ICoreWebView2BasicAuthenticationRequestedEventArgs.get_Challenge
- ICoreWebView2BasicAuthenticationRequestedEventArgs.get_Response
- ICoreWebView2BasicAuthenticationRequestedEventArgs.get_Uri
- ICoreWebView2BasicAuthenticationRequestedEventArgs.GetDeferral
- ICoreWebView2BasicAuthenticationRequestedEventArgs.put_Cancel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BasicAuthenticationRequestedEventArgs

```
interface ICoreWebView2BasicAuthenticationRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_Challenge](#get_challenge) | Gets the `Challenge` property.
[get_Response](#get_response) | Gets the `Response` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[GetDeferral](#getdeferral) | 
[put_Cancel](#put_cancel) | Sets the `Cancel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_Cancel

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_Challenge

Gets the `Challenge` property.

> public HRESULT [get_Challenge](#get_challenge)(LPWSTR * value)

#### get_Response

Gets the `Response` property.

> public HRESULT [get_Response](#get_response)([ICoreWebView2BasicAuthenticationResponse](icorewebview2basicauthenticationresponse.md) ** value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

