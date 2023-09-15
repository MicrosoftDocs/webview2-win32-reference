---
description: 
title: WebView2 Win32 C++ ICoreWebView2Certificate
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Certificate
topic_type: 
- APIRef
api_name:
- ICoreWebView2Certificate
- ICoreWebView2Certificate.get_DerEncodedSerialNumber
- ICoreWebView2Certificate.get_DisplayName
- ICoreWebView2Certificate.get_Issuer
- ICoreWebView2Certificate.get_PemEncodedIssuerCertificateChain
- ICoreWebView2Certificate.get_Subject
- ICoreWebView2Certificate.get_ValidFrom
- ICoreWebView2Certificate.get_ValidTo
- ICoreWebView2Certificate.ToPemEncoding
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Certificate

```
interface ICoreWebView2Certificate
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DerEncodedSerialNumber](#get_derencodedserialnumber) | Gets the `DerEncodedSerialNumber` property.
[get_DisplayName](#get_displayname) | Gets the `DisplayName` property.
[get_Issuer](#get_issuer) | Gets the `Issuer` property.
[get_PemEncodedIssuerCertificateChain](#get_pemencodedissuercertificatechain) | Gets the `PemEncodedIssuerCertificateChain` property.
[get_Subject](#get_subject) | Gets the `Subject` property.
[get_ValidFrom](#get_validfrom) | Gets the `ValidFrom` property.
[get_ValidTo](#get_validto) | Gets the `ValidTo` property.
[ToPemEncoding](#topemencoding) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1158

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

