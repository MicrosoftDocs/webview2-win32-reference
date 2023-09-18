---
description: 
title: WebView2 Win32 C++ ICoreWebView2ClientCertificateRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClientCertificateRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ClientCertificateRequestedEventArgs
- ICoreWebView2ClientCertificateRequestedEventArgs.get_AllowedCertificateAuthorities
- ICoreWebView2ClientCertificateRequestedEventArgs.get_Cancel
- ICoreWebView2ClientCertificateRequestedEventArgs.get_Handled
- ICoreWebView2ClientCertificateRequestedEventArgs.get_Host
- ICoreWebView2ClientCertificateRequestedEventArgs.get_IsProxy
- ICoreWebView2ClientCertificateRequestedEventArgs.get_MutuallyTrustedCertificates
- ICoreWebView2ClientCertificateRequestedEventArgs.get_Port
- ICoreWebView2ClientCertificateRequestedEventArgs.get_SelectedCertificate
- ICoreWebView2ClientCertificateRequestedEventArgs.GetDeferral
- ICoreWebView2ClientCertificateRequestedEventArgs.put_Cancel
- ICoreWebView2ClientCertificateRequestedEventArgs.put_Handled
- ICoreWebView2ClientCertificateRequestedEventArgs.put_SelectedCertificate
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ClientCertificateRequestedEventArgs

```
interface ICoreWebView2ClientCertificateRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowedCertificateAuthorities](#get_allowedcertificateauthorities) | Gets the `AllowedCertificateAuthorities` property.
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_Host](#get_host) | Gets the `Host` property.
[get_IsProxy](#get_isproxy) | Gets the `IsProxy` property.
[get_MutuallyTrustedCertificates](#get_mutuallytrustedcertificates) | Gets the `MutuallyTrustedCertificates` property.
[get_Port](#get_port) | Gets the `Port` property.
[get_SelectedCertificate](#get_selectedcertificate) | Gets the `SelectedCertificate` property.
[GetDeferral](#getdeferral) | 
[put_Cancel](#put_cancel) | Sets the `Cancel` property.
[put_Handled](#put_handled) | Sets the `Handled` property.
[put_SelectedCertificate](#put_selectedcertificate) | Sets the `SelectedCertificate` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### get_AllowedCertificateAuthorities

Gets the `AllowedCertificateAuthorities` property.

> public HRESULT [get_AllowedCertificateAuthorities](#get_allowedcertificateauthorities)(LPCWSTRCollection ** value)

#### get_Cancel

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Host

Gets the `Host` property.

> public HRESULT [get_Host](#get_host)(LPWSTR * value)

#### get_IsProxy

Gets the `IsProxy` property.

> public HRESULT [get_IsProxy](#get_isproxy)(BOOL * value)

#### get_MutuallyTrustedCertificates

Gets the `MutuallyTrustedCertificates` property.

> public HRESULT [get_MutuallyTrustedCertificates](#get_mutuallytrustedcertificates)(ICoreWebView2ClientCertificateCollection ** value)

#### get_Port

Gets the `Port` property.

> public HRESULT [get_Port](#get_port)(INT32 * value)

#### get_SelectedCertificate

Gets the `SelectedCertificate` property.

> public HRESULT [get_SelectedCertificate](#get_selectedcertificate)([ICoreWebView2ClientCertificate](icorewebview2clientcertificate.md) ** value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

#### put_SelectedCertificate

Sets the `SelectedCertificate` property.

> public HRESULT [put_SelectedCertificate](#put_selectedcertificate)([ICoreWebView2ClientCertificate](icorewebview2clientcertificate.md) * value)

