---
description: The caller implements this interface to receive the result of setting the browser Extension as enabled or disabled.
title: WebView2 Win32 C++ ICoreWebView2BrowserExtensionEnableCompletedHandler
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserExtensionEnableCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2BrowserExtensionEnableCompletedHandler
- ICoreWebView2BrowserExtensionEnableCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BrowserExtensionEnableCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2BrowserExtensionEnableCompletedHandler
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
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Provides the result of the browser extension enable operation.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

