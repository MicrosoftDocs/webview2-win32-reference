---
description: An event handler for the `ServerCertificateErrorDetected` event.
title: WebView2 Win32 C++ ICoreWebView2ServerCertificateErrorDetectedEventHandler
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServerCertificateErrorDetectedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServerCertificateErrorDetectedEventHandler
- ICoreWebView2ServerCertificateErrorDetectedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServerCertificateErrorDetectedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ServerCertificateErrorDetectedEventHandler
  : public IUnknown
```

An event handler for the `ServerCertificateErrorDetected` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ServerCertificateErrorDetectedEventArgs](icorewebview2servercertificateerrordetectedeventargs.md#icorewebview2servercertificateerrordetectedeventargs) * args)

