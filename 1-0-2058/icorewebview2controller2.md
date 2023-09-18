---
description: 
title: WebView2 Win32 C++ ICoreWebView2Controller2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Controller2
- ICoreWebView2Controller2.get_DefaultBackgroundColor
- ICoreWebView2Controller2.put_DefaultBackgroundColor
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Controller2

```
interface ICoreWebView2Controller2
  : public ICoreWebView2Controller
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultBackgroundColor](#get_defaultbackgroundcolor) | Gets the `DefaultBackgroundColor` property.
[put_DefaultBackgroundColor](#put_defaultbackgroundcolor) | Sets the `DefaultBackgroundColor` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### get_DefaultBackgroundColor

Gets the `DefaultBackgroundColor` property.

> public HRESULT [get_DefaultBackgroundColor](#get_defaultbackgroundcolor)(COLOR * value)

#### put_DefaultBackgroundColor

Sets the `DefaultBackgroundColor` property.

> public HRESULT [put_DefaultBackgroundColor](#put_defaultbackgroundcolor)(COLOR value)

