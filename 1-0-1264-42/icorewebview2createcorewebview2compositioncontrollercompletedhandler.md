---
description: The caller implements this interface to receive the CoreWebView2Controller created via CreateCoreWebView2CompositionController.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
---

# interface ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler

```
interface ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the CoreWebView2Controller created via CreateCoreWebView2CompositionController.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### Invoke

Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) * webView)

