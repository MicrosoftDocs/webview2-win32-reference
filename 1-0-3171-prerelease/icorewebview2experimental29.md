---
description: Interface providing methods to access the find session functionalities in the CoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2Experimental29
ms.date: 03/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental29
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental29
- ICoreWebView2Experimental29.get_Find
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental29

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental29
  : public IUnknown
```

Interface providing methods to access the find session functionalities in the CoreWebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Find](#get_find) | Retrieves the find session interface for the current web view.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### get_Find

Retrieves the find session interface for the current web view.

> public HRESULT [get_Find](#get_find)([ICoreWebView2ExperimentalFind](icorewebview2experimentalfind.md#icorewebview2experimentalfind) ** value)

