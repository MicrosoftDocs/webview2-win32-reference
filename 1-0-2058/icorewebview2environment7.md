---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment7
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment7
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment7
- ICoreWebView2Environment7.get_UserDataFolder
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment7

```
interface ICoreWebView2Environment7
  : public ICoreWebView2Environment6
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserDataFolder](#get_userdatafolder) | Gets the `UserDataFolder` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1054.31
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### get_UserDataFolder

Gets the `UserDataFolder` property.

> public HRESULT [get_UserDataFolder](#get_userdatafolder)(LPWSTR * value)

