---
description: Read-only collection of generic objects.
title: WebView2 Win32 C++ ICoreWebView2ObjectCollectionView
ms.date: 05/02/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ObjectCollectionView
---

# interface ICoreWebView2ObjectCollectionView

```
interface ICoreWebView2ObjectCollectionView
  : public IUnknown
```

Read-only collection of generic objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | Gets the number of items in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the object at the specified index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_Count

Gets the number of items in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the object at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, IUnknown ** value)

Cast the object to the native type to access its specific properties.

