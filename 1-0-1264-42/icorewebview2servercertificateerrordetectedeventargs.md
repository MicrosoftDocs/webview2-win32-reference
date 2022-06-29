---
description: Event args for the `ServerCertificateErrorDetected` event.
title: WebView2 Win32 C++ ICoreWebView2ServerCertificateErrorDetectedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServerCertificateErrorDetectedEventArgs
---

# interface ICoreWebView2ServerCertificateErrorDetectedEventArgs

```
interface ICoreWebView2ServerCertificateErrorDetectedEventArgs
  : public IUnknown
```

Event args for the `ServerCertificateErrorDetected` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Action](#get_action) | The action of the server certificate error detection.
[get_ErrorStatus](#get_errorstatus) | The TLS error code for the invalid certificate.
[get_RequestUri](#get_requesturi) | URI associated with the request for the invalid certificate.
[get_ServerCertificate](#get_servercertificate) | Returns the server certificate.
[GetDeferral](#getdeferral) | Returns an ICoreWebView2Deferral object.
[put_Action](#put_action) | Sets the `Action` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_Action

The action of the server certificate error detection.

> public HRESULT [get_Action](#get_action)(COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION * value)

The default value is `COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_DEFAULT`.

#### get_ErrorStatus

The TLS error code for the invalid certificate.

> public HRESULT [get_ErrorStatus](#get_errorstatus)(COREWEBVIEW2_WEB_ERROR_STATUS * value)

#### get_RequestUri

URI associated with the request for the invalid certificate.

> public HRESULT [get_RequestUri](#get_requesturi)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ServerCertificate

Returns the server certificate.

> public HRESULT [get_ServerCertificate](#get_servercertificate)(ICoreWebView2Certificate ** value)

#### GetDeferral

Returns an ICoreWebView2Deferral object.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use this operation to complete the event at a later time.

#### put_Action

Sets the `Action` property.

> public HRESULT [put_Action](#put_action)(COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION value)

