---
description: The caller implements this interface to receive the result of removing the browser Extension from the Profile.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBrowserExtensionRemoveCompletedHandler
ms.date: 08/28/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBrowserExtensionRemoveCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalBrowserExtensionRemoveCompletedHandler
- ICoreWebView2ExperimentalBrowserExtensionRemoveCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalBrowserExtensionRemoveCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBrowserExtensionRemoveCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the result of removing the browser Extension from the Profile.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the browser extension Remove operation.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### Invoke

Provides the result of the browser extension Remove operation.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode)

