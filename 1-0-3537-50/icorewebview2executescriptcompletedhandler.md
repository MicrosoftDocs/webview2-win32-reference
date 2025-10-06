---
description: Receives the result of the `ExecuteScript` method.
title: WebView2 Win32 C++ ICoreWebView2ExecuteScriptCompletedHandler
ms.date: 09/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExecuteScriptCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExecuteScriptCompletedHandler
- ICoreWebView2ExecuteScriptCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExecuteScriptCompletedHandler

```
interface ICoreWebView2ExecuteScriptCompletedHandler
  : public IUnknown
```

Receives the result of the `ExecuteScript` method.

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

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, LPCWSTR result)

