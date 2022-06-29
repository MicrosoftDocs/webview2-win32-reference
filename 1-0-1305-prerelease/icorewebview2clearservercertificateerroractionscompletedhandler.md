---
description: Receives the result of the `ClearServerCertificateErrorActions` method.
title: WebView2 Win32 C++ ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler
---

# interface ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler

```
interface ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler
  : public IUnknown
```

Receives the result of the `ClearServerCertificateErrorActions` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

