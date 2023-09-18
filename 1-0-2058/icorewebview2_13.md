---
description: 
title: WebView2 Win32 C++ ICoreWebView2_13
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_13
topic_type: 
- APIRef
api_name:
- ICoreWebView2_13
- ICoreWebView2_13.get_Profile
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_13

```
interface ICoreWebView2_13
  : public ICoreWebView2_12
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Profile](#get_profile) | Gets the `Profile` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1210.39
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_Profile

Gets the `Profile` property.

> public HRESULT [get_Profile](#get_profile)([ICoreWebView2Profile](icorewebview2profile.md) ** value)

