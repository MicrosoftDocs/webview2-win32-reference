---
description: Receives the result of the `AddScriptToExecuteOnDocumentCreated` method.
title: WebView2 Win32 C++ ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
---

# interface ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler 

```
interface ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
  : public IUnknown
```

Receives the result of the `AddScriptToExecuteOnDocumentCreated` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provide the completion status and result of the corresponding asynchronous method.

## Members

#### Invoke 

Provide the completion status and result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, LPCWSTR id)

