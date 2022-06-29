---
description: The caller implements this interface to receive the ClearBrowsingData result.
title: WebView2 Win32 C++ ICoreWebView2ClearBrowsingDataCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ClearBrowsingDataCompletedHandler
---

# interface ICoreWebView2ClearBrowsingDataCompletedHandler

```
interface ICoreWebView2ClearBrowsingDataCompletedHandler
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
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### Invoke

Provide the completion status of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

