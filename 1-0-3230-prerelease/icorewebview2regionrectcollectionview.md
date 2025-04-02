---
description: A collection of RECT.
title: WebView2 Win32 C++ ICoreWebView2RegionRectCollectionView
ms.date: 04/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2RegionRectCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2RegionRectCollectionView
- ICoreWebView2RegionRectCollectionView.get_Count
- ICoreWebView2RegionRectCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2RegionRectCollectionView

```
interface ICoreWebView2RegionRectCollectionView
  : public IUnknown
```

A collection of RECT.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2420.47
WebView2 Win32 Prerelease |    1.0.2415

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, RECT * value)

