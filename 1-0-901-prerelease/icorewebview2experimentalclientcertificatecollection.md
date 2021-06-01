---
description: A collection of client certificate object.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClientCertificateCollection
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/01/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalClientCertificateCollection
---

# interface ICoreWebView2ExperimentalClientCertificateCollection

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClientCertificateCollection
  : public IUnknown
```

A collection of client certificate object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of client certificates contained in the ICoreWebView2ExperimentalClientCertificateCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the certificate object at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.901

## Members

#### get_Count

The number of client certificates contained in the ICoreWebView2ExperimentalClientCertificateCollection.

> public HRESULT [get_Count](#get_count)(UINT * value)

#### GetValueAtIndex

Gets the certificate object at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, ICoreWebView2ExperimentalClientCertificate ** certificate)

