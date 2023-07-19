---
description: Provides a set of properties for managing browser Extension Lists from user profile.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBrowserExtensionList
ms.date: 07/19/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBrowserExtensionList
---

# interface ICoreWebView2ExperimentalBrowserExtensionList

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBrowserExtensionList
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Count

The number of browser Extensions in the list.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the browser Extension located in the browser Extension List at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT index, ICoreWebView2ExperimentalBrowserExtension ** extension)

