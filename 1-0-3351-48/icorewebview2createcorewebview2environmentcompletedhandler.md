---
description: Receives the result of the `CreateCoreWebView2Environment` method.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
- ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
  : public IUnknown
```

Receives the result of the `CreateCoreWebView2Environment` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) * result)

