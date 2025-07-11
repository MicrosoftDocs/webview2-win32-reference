---
description: Receives the result of the `CreateCoreWebView2Controller` method.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
ms.date: 05/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
- ICoreWebView2CreateCoreWebView2ControllerCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CreateCoreWebView2ControllerCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CreateCoreWebView2ControllerCompletedHandler
  : public IUnknown
```

Receives the result of the `CreateCoreWebView2Controller` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.488
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2Controller](icorewebview2controller.md#icorewebview2controller) * result)

