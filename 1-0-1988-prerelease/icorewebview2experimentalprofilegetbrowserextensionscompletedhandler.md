---
description: The caller implements this interface to receive the result of getting the browser Extensions.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler
ms.date: 07/25/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler
- ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the result of getting the browser Extensions.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the browser extension list for the requested user profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### Invoke

Provides the browser extension list for the requested user profile.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalBrowserExtensionList](icorewebview2experimentalbrowserextensionlist.md) * extensionList)

