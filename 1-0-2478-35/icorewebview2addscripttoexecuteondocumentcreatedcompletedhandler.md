---
description: Receives the result of the `AddScriptToExecuteOnDocumentCreated` method.
title: WebView2 Win32 C++ ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
ms.date: 05/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
- ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2AddScriptToExecuteOnDocumentCreatedCompletedHandler
  : public IUnknown
```

Receives the result of the `AddScriptToExecuteOnDocumentCreated` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provide the completion status and result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provide the completion status and result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, LPCWSTR id)

