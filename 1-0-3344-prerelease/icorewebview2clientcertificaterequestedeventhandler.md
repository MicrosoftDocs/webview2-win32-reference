---
description: Receives `ClientCertificateRequested` events.
title: WebView2 Win32 C++ ICoreWebView2ClientCertificateRequestedEventHandler
ms.date: 05/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClientCertificateRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ClientCertificateRequestedEventHandler
- ICoreWebView2ClientCertificateRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ClientCertificateRequestedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ClientCertificateRequestedEventHandler
  : public IUnknown
```

Receives `ClientCertificateRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ClientCertificateRequestedEventArgs](icorewebview2clientcertificaterequestedeventargs.md#icorewebview2clientcertificaterequestedeventargs) * args)

