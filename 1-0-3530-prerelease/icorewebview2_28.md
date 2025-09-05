---
description: Interface providing methods to access the find session functionalities in the CoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2_28
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_28
topic_type: 
- APIRef
api_name:
- ICoreWebView2_28
- ICoreWebView2_28.get_Find
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_28

```
interface ICoreWebView2_28
  : public ICoreWebView2_27
```

Interface providing methods to access the find session functionalities in the CoreWebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Find](#get_find) | Retrieves the find session interface for the current web view.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3405.78
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### get_Find

Retrieves the find session interface for the current web view.

> public HRESULT [get_Find](#get_find)([ICoreWebView2Find](icorewebview2find.md#icorewebview2find) ** value)

