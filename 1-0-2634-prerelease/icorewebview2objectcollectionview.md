---
description: A collection of IUnknown.
title: WebView2 Win32 C++ ICoreWebView2ObjectCollectionView
ms.date: 06/05/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ObjectCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ObjectCollectionView
- ICoreWebView2ObjectCollectionView.get_Count
- ICoreWebView2ObjectCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ObjectCollectionView

```
interface ICoreWebView2ObjectCollectionView
  : public IUnknown
```

A collection of IUnknown.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, IUnknown ** value)

