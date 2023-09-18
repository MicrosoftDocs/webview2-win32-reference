---
description: 
title: WebView2 Win32 C++ ICoreWebView2ClientCertificate
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClientCertificate
topic_type: 
- APIRef
api_name:
- ICoreWebView2ClientCertificate
- ICoreWebView2ClientCertificate.get_DerEncodedSerialNumber
- ICoreWebView2ClientCertificate.get_DisplayName
- ICoreWebView2ClientCertificate.get_Issuer
- ICoreWebView2ClientCertificate.get_Kind
- ICoreWebView2ClientCertificate.get_PemEncodedIssuerCertificateChain
- ICoreWebView2ClientCertificate.get_Subject
- ICoreWebView2ClientCertificate.get_ValidFrom
- ICoreWebView2ClientCertificate.get_ValidTo
- ICoreWebView2ClientCertificate.ToPemEncoding
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ClientCertificate

```
interface ICoreWebView2ClientCertificate
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DerEncodedSerialNumber](#get_derencodedserialnumber) | Gets the `DerEncodedSerialNumber` property.
[get_DisplayName](#get_displayname) | Gets the `DisplayName` property.
[get_Issuer](#get_issuer) | Gets the `Issuer` property.
[get_Kind](#get_kind) | Gets the `Kind` property.
[get_PemEncodedIssuerCertificateChain](#get_pemencodedissuercertificatechain) | Gets the `PemEncodedIssuerCertificateChain` property.
[get_Subject](#get_subject) | Gets the `Subject` property.
[get_ValidFrom](#get_validfrom) | Gets the `ValidFrom` property.
[get_ValidTo](#get_validto) | Gets the `ValidTo` property.
[ToPemEncoding](#topemencoding) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### get_DerEncodedSerialNumber

Gets the `DerEncodedSerialNumber` property.

> public HRESULT [get_DerEncodedSerialNumber](#get_derencodedserialnumber)(LPWSTR * value)

#### get_DisplayName

Gets the `DisplayName` property.

> public HRESULT [get_DisplayName](#get_displayname)(LPWSTR * value)

#### get_Issuer

Gets the `Issuer` property.

> public HRESULT [get_Issuer](#get_issuer)(LPWSTR * value)

#### get_Kind

Gets the `Kind` property.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_CLIENT_CERTIFICATE_KIND * value)

#### get_PemEncodedIssuerCertificateChain

Gets the `PemEncodedIssuerCertificateChain` property.

> public HRESULT [get_PemEncodedIssuerCertificateChain](#get_pemencodedissuercertificatechain)(LPCWSTRCollection ** value)

#### get_Subject

Gets the `Subject` property.

> public HRESULT [get_Subject](#get_subject)(LPWSTR * value)

#### get_ValidFrom

Gets the `ValidFrom` property.

> public HRESULT [get_ValidFrom](#get_validfrom)(double * value)

#### get_ValidTo

Gets the `ValidTo` property.

> public HRESULT [get_ValidTo](#get_validto)(double * value)

#### ToPemEncoding

> public HRESULT [ToPemEncoding](#topemencoding)(LPWSTR * value)

