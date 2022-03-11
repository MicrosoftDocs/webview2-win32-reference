---
description: A collection of certificate object.
title: WebView2 Win32 C++ ICoreWebView2CertificateCollection
ms.date: 03/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CertificateCollection
---

# interface ICoreWebView2CertificateCollection

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CertificateCollection
  : public IUnknown
```

A collection of certificate object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of certificates contained in the ICoreWebView2CertificateCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the certificate object at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### get_Count

The number of certificates contained in the ICoreWebView2CertificateCollection.

> public HRESULT [get_Count](#get_count)(UINT * value)

#### GetValueAtIndex

Gets the certificate object at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, ICoreWebView2Certificate ** certificate)

