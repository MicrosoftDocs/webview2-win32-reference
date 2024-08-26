---
description: Receives the result of the `GetBrowserExtensions` method.
title: WebView2 Win32 C++ ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler
ms.date: 08/26/2024
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler
  : public IUnknown
```

Receives the result of the `GetBrowserExtensions` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2BrowserExtensionList](icorewebview2browserextensionlist.md#icorewebview2browserextensionlist) * result)

