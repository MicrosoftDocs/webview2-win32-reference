---
description: A collection of strings.
title: WebView2 Win32 C++ ICoreWebView2StringCollection
ms.date: 10/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2StringCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2StringCollection
- ICoreWebView2StringCollection.get_Count
- ICoreWebView2StringCollection.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2StringCollection

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2StringCollection
  : public IUnknown
```

A collection of strings.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of strings contained in ICoreWebView2StringCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the value at a given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### get_Count

The number of strings contained in ICoreWebView2StringCollection.

> public HRESULT [get_Count](#get_count)(UINT * value)

#### GetValueAtIndex

Gets the value at a given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

