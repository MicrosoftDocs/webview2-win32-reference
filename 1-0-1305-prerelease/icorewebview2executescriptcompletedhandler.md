---
description: Receives the result of the `ExecuteScript` method.
title: WebView2 Win32 C++ ICoreWebView2ExecuteScriptCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExecuteScriptCompletedHandler
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
[Invoke](#invoke) | Provide the implementer with the completion status and result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provide the implementer with the completion status and result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, LPCWSTR resultObjectAsJson)

