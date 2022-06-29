---
description: Event args for the BasicAuthenticationRequested event.
title: WebView2 Win32 C++ ICoreWebView2BasicAuthenticationRequestedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BasicAuthenticationRequestedEventArgs
---

# interface ICoreWebView2BasicAuthenticationRequestedEventArgs

```
interface ICoreWebView2BasicAuthenticationRequestedEventArgs
  : public IUnknown
```

Event args for the BasicAuthenticationRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Cancel the authentication request.
[get_Challenge](#get_challenge) | The authentication challenge string.
[get_Response](#get_response) | Response to the authentication request with credentials.
[get_Uri](#get_uri) | The URI that led to the authentication challenge.
[GetDeferral](#getdeferral) | Returns an ICoreWebView2Deferral object.
[put_Cancel](#put_cancel) | Set the Cancel property.

Will contain the request that led to the HTTP authorization challenge, the challenge and allows the host to provide authentication response or cancel the request.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_Cancel

Cancel the authentication request.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * cancel)

False by default. If set to true, Response will be ignored.

#### get_Challenge

The authentication challenge string.

> public HRESULT [get_Challenge](#get_challenge)(LPWSTR * challenge)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Response

Response to the authentication request with credentials.

> public HRESULT [get_Response](#get_response)(ICoreWebView2BasicAuthenticationResponse ** response)

This object will be populated by the app if the host would like to provide authentication credentials.

#### get_Uri

The URI that led to the authentication challenge.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetDeferral

Returns an ICoreWebView2Deferral object.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use this deferral to defer the decision to show the Basic Authentication dialog.

#### put_Cancel

Set the Cancel property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL cancel)

