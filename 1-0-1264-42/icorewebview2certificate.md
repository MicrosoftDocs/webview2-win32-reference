---
description: Provides access to the certificate metadata.
title: WebView2 Win32 C++ ICoreWebView2Certificate
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Certificate
---

# interface ICoreWebView2Certificate

```
interface ICoreWebView2Certificate
  : public IUnknown
```

Provides access to the certificate metadata.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DerEncodedSerialNumber](#get_derencodedserialnumber) | DER encoded serial number of the certificate.
[get_DisplayName](#get_displayname) | Display name for a certificate.
[get_Issuer](#get_issuer) | Name of the certificate authority that issued the certificate.
[get_PemEncodedIssuerCertificateChain](#get_pemencodedissuercertificatechain) | Collection of PEM encoded certificate issuer chain.
[get_Subject](#get_subject) | Subject of the certificate.
[get_ValidFrom](#get_validfrom) | The valid start date and time for the certificate as the number of seconds since the UNIX epoch.
[get_ValidTo](#get_validto) | The valid expiration date and time for the certificate as the number of seconds since the UNIX epoch.
[ToPemEncoding](#topemencoding) | PEM encoded data for the certificate.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### get_DerEncodedSerialNumber

DER encoded serial number of the certificate.

> public HRESULT [get_DerEncodedSerialNumber](#get_derencodedserialnumber)(LPWSTR * value)

Read more about DER at [RFC 7468 DER] (https://tools.ietf.org/html/rfc7468#appendix-B).

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_DisplayName

Display name for a certificate.

> public HRESULT [get_DisplayName](#get_displayname)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings)

#### get_Issuer

Name of the certificate authority that issued the certificate.

> public HRESULT [get_Issuer](#get_issuer)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_PemEncodedIssuerCertificateChain

Collection of PEM encoded certificate issuer chain.

> public HRESULT [get_PemEncodedIssuerCertificateChain](#get_pemencodedissuercertificatechain)(ICoreWebView2StringCollection ** value)

In this collection first element is the current certificate followed by intermediate1, intermediate2...intermediateN-1. Root certificate is the last element in collection.

#### get_Subject

Subject of the certificate.

> public HRESULT [get_Subject](#get_subject)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ValidFrom

The valid start date and time for the certificate as the number of seconds since the UNIX epoch.

> public HRESULT [get_ValidFrom](#get_validfrom)(double * value)

#### get_ValidTo

The valid expiration date and time for the certificate as the number of seconds since the UNIX epoch.

> public HRESULT [get_ValidTo](#get_validto)(double * value)

#### ToPemEncoding

PEM encoded data for the certificate.

> public HRESULT [ToPemEncoding](#topemencoding)(LPWSTR * pemEncodedData)

Returns Base64 encoding of DER encoded certificate. Read more about PEM at [RFC 1421 Privacy Enhanced Mail] (https://tools.ietf.org/html/rfc1421).

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings)

