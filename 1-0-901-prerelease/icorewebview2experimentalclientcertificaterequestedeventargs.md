---
description: Event args for the `ClientCertificateRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClientCertificateRequestedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/01/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalClientCertificateRequestedEventArgs
---

# interface ICoreWebView2ExperimentalClientCertificateRequestedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClientCertificateRequestedEventArgs
  : public IUnknown
```

Event args for the `ClientCertificateRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowedCertificateAuthorities](#get_allowedcertificateauthorities) | Returns the ICoreWebView2ExperimentalStringCollection.
[get_Cancel](#get_cancel) | You??may??set??this??flag??to??cancel??the??certificate selection.
[get_Handled](#get_handled) | You??may??set??this??flag??to??`TRUE` to respond to the server with or without a certificate.
[get_Host](#get_host) | Host name of the server that requested client certificate authentication.
[get_IsProxy](#get_isproxy) | Returns true if the server that issued this request is an http proxy.
[get_MutuallyTrustedCertificates](#get_mutuallytrustedcertificates) | Returns the ICoreWebView2ExperimentalClientCertificateCollection when client certificate authentication is requested.
[get_Port](#get_port) | Port of the server that requested client certificate authentication.
[get_SelectedCertificate](#get_selectedcertificate) | Returns the selected certificate.
[GetDeferral](#getdeferral) | Returns an ICoreWebView2Deferral object.
[put_Cancel](#put_cancel) | ??Sets??the??`Cancel`??property.
[put_Handled](#put_handled) | ??Sets??the??`Handled`??property.
[put_SelectedCertificate](#put_selectedcertificate) | Sets the certificate to respond to the server.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.901

## Members

#### get_AllowedCertificateAuthorities

Returns the ICoreWebView2ExperimentalStringCollection.

> public HRESULT [get_AllowedCertificateAuthorities](#get_allowedcertificateauthorities)(ICoreWebView2ExperimentalStringCollection ** value)

The collection contains distinguished names of certificate authorities allowed by the server.

#### get_Cancel

You??may??set??this??flag??to??cancel??the??certificate selection.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

If canceled, the request is aborted regardless of the `Handled` property. By default the value is `FALSE`.

#### get_Handled

You??may??set??this??flag??to??`TRUE` to respond to the server with or without a certificate.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

If this flag is `TRUE` with a `SelectedCertificate` it responds to the server with the selected certificate otherwise respond to the server without a certificate. By default the value of `Handled` and `Cancel` are `FALSE` and display default client certificate selection dialog prompt to allow the user to choose a certificate. The `SelectedCertificate` is ignored unless `Handled` is set `TRUE`.

#### get_Host

Host name of the server that requested client certificate authentication.

> public HRESULT [get_Host](#get_host)(LPWSTR * value)

Normalization rules applied to the hostname are:

* Convert to lowercase characters for ascii characters.

* Punycode is used for representing non ascii characters.

* Strip square brackets for IPV6 address.

#### get_IsProxy

Returns true if the server that issued this request is an http proxy.

> public HRESULT [get_IsProxy](#get_isproxy)(BOOL * value)

Returns false if the server is the origin server.

#### get_MutuallyTrustedCertificates

Returns the ICoreWebView2ExperimentalClientCertificateCollection when client certificate authentication is requested.

> public HRESULT [get_MutuallyTrustedCertificates](#get_mutuallytrustedcertificates)(ICoreWebView2ExperimentalClientCertificateCollection ** value)

The collection contains mutually trusted CA certificates.

#### get_Port

Port of the server that requested client certificate authentication.

> public HRESULT [get_Port](#get_port)(int * value)

#### get_SelectedCertificate

Returns the selected certificate.

> public HRESULT [get_SelectedCertificate](#get_selectedcertificate)(ICoreWebView2ExperimentalClientCertificate ** value)

#### GetDeferral

Returns an ICoreWebView2Deferral object.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use this operation to complete the event at a later time.

#### put_Cancel

??Sets??the??`Cancel`??property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

#### put_Handled

??Sets??the??`Handled`??property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

#### put_SelectedCertificate

Sets the certificate to respond to the server.

> public HRESULT [put_SelectedCertificate](#put_selectedcertificate)(ICoreWebView2ExperimentalClientCertificate * value)

