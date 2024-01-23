---
description: A collection of client certificate object.
title: WebView2 Win32 C++ ICoreWebView2ClientCertificateCollection
ms.date: 01/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClientCertificateCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2ClientCertificateCollection
- ICoreWebView2ClientCertificateCollection.get_Count
- ICoreWebView2ClientCertificateCollection.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ClientCertificateCollection

```
interface ICoreWebView2ClientCertificateCollection
  : public IUnknown
```

A collection of client certificate object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of client certificates contained in the ICoreWebView2ClientCertificateCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the certificate object at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### get_Count

The number of client certificates contained in the ICoreWebView2ClientCertificateCollection.

> public HRESULT [get_Count](#get_count)(UINT * value)

#### GetValueAtIndex

Gets the certificate object at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, ICoreWebView2ClientCertificate ** certificate)

