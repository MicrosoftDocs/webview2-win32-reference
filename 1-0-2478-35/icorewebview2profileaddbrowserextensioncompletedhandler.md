---
description: The caller implements this interface to receive the result of loading an browser Extension.
title: WebView2 Win32 C++ ICoreWebView2ProfileAddBrowserExtensionCompletedHandler
ms.date: 05/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProfileAddBrowserExtensionCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProfileAddBrowserExtensionCompletedHandler
- ICoreWebView2ProfileAddBrowserExtensionCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProfileAddBrowserExtensionCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProfileAddBrowserExtensionCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the result of loading an browser Extension.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the `AddBrowserExtension` operation.g.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Provides the result of the `AddBrowserExtension` operation.g.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2BrowserExtension](icorewebview2browserextension.md#icorewebview2browserextension) * extension)

