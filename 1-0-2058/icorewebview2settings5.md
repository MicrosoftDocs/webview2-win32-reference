---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings5
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings5
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings5
- ICoreWebView2Settings5.get_IsPinchZoomEnabled
- ICoreWebView2Settings5.put_IsPinchZoomEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings5

```
interface ICoreWebView2Settings5
  : public ICoreWebView2Settings4
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsPinchZoomEnabled](#get_ispinchzoomenabled) | Gets the `IsPinchZoomEnabled` property.
[put_IsPinchZoomEnabled](#put_ispinchzoomenabled) | Sets the `IsPinchZoomEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_IsPinchZoomEnabled

Gets the `IsPinchZoomEnabled` property.

> public HRESULT [get_IsPinchZoomEnabled](#get_ispinchzoomenabled)(BOOL * value)

#### put_IsPinchZoomEnabled

Sets the `IsPinchZoomEnabled` property.

> public HRESULT [put_IsPinchZoomEnabled](#put_ispinchzoomenabled)(BOOL value)

