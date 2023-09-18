---
description: 
title: WebView2 Win32 C++ ICoreWebView2_5
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_5
topic_type: 
- APIRef
api_name:
- ICoreWebView2_5
- ICoreWebView2_5.add_ClientCertificateRequested
- ICoreWebView2_5.remove_ClientCertificateRequested
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_5

```
interface ICoreWebView2_5
  : public ICoreWebView2_4
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ClientCertificateRequested](#add_clientcertificaterequested) | Adds an event handler for the `ClientCertificateRequested` event.
[remove_ClientCertificateRequested](#remove_clientcertificaterequested) | Removes an event handler previously added with `add_ClientCertificateRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### add_ClientCertificateRequested

Adds an event handler for the `ClientCertificateRequested` event.

> public HRESULT [add_ClientCertificateRequested](#add_clientcertificaterequested)([ICoreWebView2ClientCertificateRequestedEventHandler](icorewebview2clientcertificaterequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_ClientCertificateRequested

Removes an event handler previously added with `add_ClientCertificateRequested`.

> public HRESULT [remove_ClientCertificateRequested](#remove_clientcertificaterequested)(EventRegistrationToken token)

