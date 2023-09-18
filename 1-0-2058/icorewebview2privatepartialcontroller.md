---
description: 
title: WebView2 Win32 C++ ICoreWebView2PrivatePartialController
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrivatePartialController
topic_type: 
- APIRef
api_name:
- ICoreWebView2PrivatePartialController
- ICoreWebView2PrivatePartialController.get_IsBrowserHitTransparent
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PrivatePartialController

```
interface ICoreWebView2PrivatePartialController
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsBrowserHitTransparent](#get_isbrowserhittransparent) | Gets the `IsBrowserHitTransparent` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_IsBrowserHitTransparent

Gets the `IsBrowserHitTransparent` property.

> public HRESULT [get_IsBrowserHitTransparent](#get_isbrowserhittransparent)(BOOL * value)

