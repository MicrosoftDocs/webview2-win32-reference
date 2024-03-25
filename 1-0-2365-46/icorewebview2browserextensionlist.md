---
description: Provides a set of properties for managing browser Extension Lists from user profile.
title: WebView2 Win32 C++ ICoreWebView2BrowserExtensionList
ms.date: 03/25/2024
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

Provides a set of properties for managing browser Extension Lists from user profile.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of browser Extensions in the list.
[GetValueAtIndex](#getvalueatindex) | Gets the browser Extension located in the browser Extension List at the given index.

This includes the number of browser Extensions in the list, and the ability to get an browser Extension from the list at a particular index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### get_Count

The number of browser Extensions in the list.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the browser Extension located in the browser Extension List at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, ICoreWebView2BrowserExtension ** extension)

