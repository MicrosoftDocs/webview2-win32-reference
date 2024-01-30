---
description: The caller implements this interface to receive the result of getting the browser Extensions.
title: WebView2 Win32 C++ ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler
ms.date: 02/05/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler
- ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler

```
interface ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler
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
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Provides the browser extension list for the requested user profile.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2BrowserExtensionList](icorewebview2browserextensionlist.md) * extensionList)

