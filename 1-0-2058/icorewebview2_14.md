---
description: 
title: WebView2 Win32 C++ ICoreWebView2_14
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_14
topic_type: 
- APIRef
api_name:
- ICoreWebView2_14
- ICoreWebView2_14.add_ServerCertificateErrorDetected
- ICoreWebView2_14.ClearServerCertificateErrorActions
- ICoreWebView2_14.remove_ServerCertificateErrorDetected
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_14

```
interface ICoreWebView2_14
  : public ICoreWebView2_13
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ServerCertificateErrorDetected](#add_servercertificateerrordetected) | Adds an event handler for the `ServerCertificateErrorDetected` event.
[ClearServerCertificateErrorActions](#clearservercertificateerroractions) | 
[remove_ServerCertificateErrorDetected](#remove_servercertificateerrordetected) | Removes an event handler previously added with `add_ServerCertificateErrorDetected`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### add_ServerCertificateErrorDetected

Adds an event handler for the `ServerCertificateErrorDetected` event.

> public HRESULT [add_ServerCertificateErrorDetected](#add_servercertificateerrordetected)([ICoreWebView2ServerCertificateErrorDetectedEventHandler](icorewebview2servercertificateerrordetectedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### ClearServerCertificateErrorActions

> public HRESULT [ClearServerCertificateErrorActions](#clearservercertificateerroractions)([ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler](icorewebview2clearservercertificateerroractionscompletedhandler.md) * handler)

#### remove_ServerCertificateErrorDetected

Removes an event handler previously added with `add_ServerCertificateErrorDetected`.

> public HRESULT [remove_ServerCertificateErrorDetected](#remove_servercertificateerrordetected)(EventRegistrationToken token)

