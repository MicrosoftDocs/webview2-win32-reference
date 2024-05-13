---
description: This Interface Represents a Collection of Region Rects.
title: WebView2 Win32 C++ ICoreWebView2RegionRectCollectionView
ms.date: 05/13/2024
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

This Interface Represents a Collection of Region Rects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | This method gets the number of Rects contained in the collection.
[GetValueAtIndex](#getvalueatindex) | This method gets the Rect at the specified index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2420.47
WebView2 Win32 Prerelease |    1.0.2415

## Members

#### get_Count

This method gets the number of Rects contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

This method gets the Rect at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, RECT * value)

