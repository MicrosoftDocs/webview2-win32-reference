---
description: A collection of ICoreWebView2BrowserExtension.
title: WebView2 Win32 C++ ICoreWebView2BrowserExtensionList
ms.date: 01/16/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserExtensionList
topic_type: 
- APIRef
api_name:
- ICoreWebView2BrowserExtensionList
- ICoreWebView2BrowserExtensionList.get_Count
- ICoreWebView2BrowserExtensionList.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BrowserExtensionList

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2BrowserExtensionList
  : public IUnknown
```

A collection of [ICoreWebView2BrowserExtension](icorewebview2browserextension.md#icorewebview2browserextension).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2BrowserExtension](icorewebview2browserextension.md#icorewebview2browserextension) ** value)

