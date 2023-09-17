---
description: The caller implements this interface to handle the result of `SetPermissionState`.
title: WebView2 Win32 C++ ICoreWebView2SetPermissionStateCompletedHandler
ms.date: 09/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SetPermissionStateCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2SetPermissionStateCompletedHandler
- ICoreWebView2SetPermissionStateCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SetPermissionStateCompletedHandler

```
interface ICoreWebView2SetPermissionStateCompletedHandler
  : public IUnknown
```

The caller implements this interface to handle the result of `SetPermissionState`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provide the completion status of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### Invoke

Provide the completion status of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

