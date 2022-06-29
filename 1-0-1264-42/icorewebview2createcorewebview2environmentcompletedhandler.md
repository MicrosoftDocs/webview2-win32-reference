---
description: Receives the `WebView2Environment` created using `CreateCoreWebView2Environment`.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
---

# interface ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler

```
interface ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
  : public IUnknown
```

Receives the `WebView2Environment` created using `CreateCoreWebView2Environment`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the completion status and result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the completion status and result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2Environment](icorewebview2environment.md) * createdEnvironment)

