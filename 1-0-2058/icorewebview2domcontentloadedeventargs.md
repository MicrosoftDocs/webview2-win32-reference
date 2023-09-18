---
description: 
title: WebView2 Win32 C++ ICoreWebView2DOMContentLoadedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DOMContentLoadedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2DOMContentLoadedEventArgs
- ICoreWebView2DOMContentLoadedEventArgs.get_NavigationId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DOMContentLoadedEventArgs

```
interface ICoreWebView2DOMContentLoadedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_NavigationId](#get_navigationid) | Gets the `NavigationId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### get_NavigationId

Gets the `NavigationId` property.

> public HRESULT [get_NavigationId](#get_navigationid)(UINT64 * value)

