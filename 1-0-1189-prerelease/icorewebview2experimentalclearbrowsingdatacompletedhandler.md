---
description: The caller implements this interface to receive the ClearBrowsingData result.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClearBrowsingDataCompletedHandler
ms.date: 04/12/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalClearBrowsingDataCompletedHandler
---

# interface ICoreWebView2ExperimentalClearBrowsingDataCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClearBrowsingDataCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the ClearBrowsingData result.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provide the completion status of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### Invoke

Provide the completion status of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

