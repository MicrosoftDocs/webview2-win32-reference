---
description: Receives the result of the `GetServiceWorkerRegistrations` method.
title: WebView2 Win32 C++ ICoreWebView2GetServiceWorkerRegistrationsCompletedHandler
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetServiceWorkerRegistrationsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2GetServiceWorkerRegistrationsCompletedHandler
- ICoreWebView2GetServiceWorkerRegistrationsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2GetServiceWorkerRegistrationsCompletedHandler

```
interface ICoreWebView2GetServiceWorkerRegistrationsCompletedHandler
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
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ServiceWorkerRegistrationCollectionView](icorewebview2serviceworkerregistrationcollectionview.md#icorewebview2serviceworkerregistrationcollectionview) * result)

