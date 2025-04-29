---
description: Receives the result of the `CreateCoreWebView2CompositionController` method.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
- ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler

```
interface ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
  : public IUnknown
```

Receives the result of the `CreateCoreWebView2CompositionController` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) * result)

