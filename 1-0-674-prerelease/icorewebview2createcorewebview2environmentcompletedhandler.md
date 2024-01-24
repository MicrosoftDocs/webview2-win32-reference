---
description: The caller implements this interface to receive the WebView2Environment created via CreateCoreWebView2Environment.
title: WebView2 Win32 C++ ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
---

# interface ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the WebView2Environment created via CreateCoreWebView2Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

## Members

#### Invoke 

Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2Environment](icorewebview2environment.md) * createdEnvironment)

