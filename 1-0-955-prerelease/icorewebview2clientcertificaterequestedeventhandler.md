---
description: An event handler for the `ClientCertificateRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ClientCertificateRequestedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/26/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClientCertificateRequestedEventHandler
---

# interface ICoreWebView2ClientCertificateRequestedEventHandler

```
interface ICoreWebView2ClientCertificateRequestedEventHandler
  : public IUnknown
```

An event handler for the `ClientCertificateRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.955

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2ClientCertificateRequestedEventArgs * args)

