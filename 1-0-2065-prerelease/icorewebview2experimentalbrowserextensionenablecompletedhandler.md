---
description: The caller implements this interface to receive the result of setting the browser Extension as enabled or disabled.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBrowserExtensionEnableCompletedHandler
ms.date: 08/30/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBrowserExtensionEnableCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalBrowserExtensionEnableCompletedHandler
- ICoreWebView2ExperimentalBrowserExtensionEnableCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalBrowserExtensionEnableCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBrowserExtensionEnableCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the result of setting the browser Extension as enabled or disabled.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the browser extension enable operation.

If enabled, the browser Extension is running in WebView instances. If disabled, the browser Extension is not running in WebView instances.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### Invoke

Provides the result of the browser extension enable operation.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

