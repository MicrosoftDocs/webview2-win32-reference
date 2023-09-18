---
description: 
title: WebView2 Win32 C++ ICoreWebView2ServerCertificateErrorDetectedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServerCertificateErrorDetectedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServerCertificateErrorDetectedEventArgs
- ICoreWebView2ServerCertificateErrorDetectedEventArgs.get_Action
- ICoreWebView2ServerCertificateErrorDetectedEventArgs.get_ErrorStatus
- ICoreWebView2ServerCertificateErrorDetectedEventArgs.get_RequestUri
- ICoreWebView2ServerCertificateErrorDetectedEventArgs.get_ServerCertificate
- ICoreWebView2ServerCertificateErrorDetectedEventArgs.GetDeferral
- ICoreWebView2ServerCertificateErrorDetectedEventArgs.put_Action
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServerCertificateErrorDetectedEventArgs

```
interface ICoreWebView2ServerCertificateErrorDetectedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Action](#get_action) | Gets the `Action` property.
[get_ErrorStatus](#get_errorstatus) | Gets the `ErrorStatus` property.
[get_RequestUri](#get_requesturi) | Gets the `RequestUri` property.
[get_ServerCertificate](#get_servercertificate) | Gets the `ServerCertificate` property.
[GetDeferral](#getdeferral) | 
[put_Action](#put_action) | Sets the `Action` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_Action

Gets the `Action` property.

> public HRESULT [get_Action](#get_action)(COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION * value)

#### get_ErrorStatus

Gets the `ErrorStatus` property.

> public HRESULT [get_ErrorStatus](#get_errorstatus)(COREWEBVIEW2_WEB_ERROR_STATUS * value)

#### get_RequestUri

Gets the `RequestUri` property.

> public HRESULT [get_RequestUri](#get_requesturi)(LPWSTR * value)

#### get_ServerCertificate

Gets the `ServerCertificate` property.

> public HRESULT [get_ServerCertificate](#get_servercertificate)([ICoreWebView2Certificate](icorewebview2certificate.md) ** value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Action

Sets the `Action` property.

> public HRESULT [put_Action](#put_action)(COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION value)

