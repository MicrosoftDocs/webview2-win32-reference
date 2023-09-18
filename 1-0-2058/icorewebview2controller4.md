---
description: 
title: WebView2 Win32 C++ ICoreWebView2Controller4
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller4
topic_type: 
- APIRef
api_name:
- ICoreWebView2Controller4
- ICoreWebView2Controller4.get_AllowExternalDrop
- ICoreWebView2Controller4.put_AllowExternalDrop
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Controller4

```
interface ICoreWebView2Controller4
  : public ICoreWebView2Controller3
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowExternalDrop](#get_allowexternaldrop) | Gets the `AllowExternalDrop` property.
[put_AllowExternalDrop](#put_allowexternaldrop) | Sets the `AllowExternalDrop` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_AllowExternalDrop

Gets the `AllowExternalDrop` property.

> public HRESULT [get_AllowExternalDrop](#get_allowexternaldrop)(BOOL * value)

#### put_AllowExternalDrop

Sets the `AllowExternalDrop` property.

> public HRESULT [put_AllowExternalDrop](#put_allowexternaldrop)(BOOL value)

