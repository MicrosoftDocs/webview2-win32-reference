---
description: This is the callback for ExecuteScriptWithResult.
title: WebView2 Win32 C++ ICoreWebView2ExecuteScriptWithResultCompletedHandler
ms.date: 05/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExecuteScriptWithResultCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExecuteScriptWithResultCompletedHandler
- ICoreWebView2ExecuteScriptWithResultCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExecuteScriptWithResultCompletedHandler

```
interface ICoreWebView2ExecuteScriptWithResultCompletedHandler
  : public IUnknown
```

This is the callback for ExecuteScriptWithResult.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of ExecuteScriptWithResult.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2277.86
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### Invoke

Provides the result of ExecuteScriptWithResult.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExecuteScriptResult](icorewebview2executescriptresult.md#icorewebview2executescriptresult) * result)

