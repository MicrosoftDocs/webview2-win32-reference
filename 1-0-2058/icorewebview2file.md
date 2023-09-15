---
description: 
title: WebView2 Win32 C++ ICoreWebView2File
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2File
topic_type: 
- APIRef
api_name:
- ICoreWebView2File
- ICoreWebView2File.get_Path
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2File

```
interface ICoreWebView2File
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Path](#get_path) | Gets the `Path` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_Path

Gets the `Path` property.

> public HRESULT [get_Path](#get_path)(LPWSTR * value)

