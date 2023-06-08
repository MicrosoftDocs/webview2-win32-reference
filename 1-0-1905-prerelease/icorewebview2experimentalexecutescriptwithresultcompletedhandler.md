---
description: This is the callback for ExecuteScriptWithResult.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalExecuteScriptWithResultCompletedHandler
ms.date: 06/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalExecuteScriptWithResultCompletedHandler
---

# interface ICoreWebView2ExperimentalExecuteScriptWithResultCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalExecuteScriptWithResultCompletedHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1466

## Members

#### Invoke

Provides the result of ExecuteScriptWithResult.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalExecuteScriptResult](icorewebview2experimentalexecutescriptresult.md) * result)

