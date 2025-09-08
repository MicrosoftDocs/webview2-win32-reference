---
description: Receives the result of the `TrySuspend` method.
title: WebView2 Win32 C++ ICoreWebView2TrySuspendCompletedHandler
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2TrySuspendCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2TrySuspendCompletedHandler
- ICoreWebView2TrySuspendCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2TrySuspendCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2TrySuspendCompletedHandler
  : public IUnknown
```

Receives the result of the `TrySuspend` method.

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

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, BOOL result)

