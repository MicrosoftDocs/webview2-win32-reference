---
description: Receives the result of the `GetServiceWorkerRegistrations` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler
- ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler
  : public IUnknown
```

Receives the result of the `GetServiceWorkerRegistrations` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView](icorewebview2experimentalserviceworkerregistrationcollectionview.md#icorewebview2experimentalserviceworkerregistrationcollectionview) * result)

