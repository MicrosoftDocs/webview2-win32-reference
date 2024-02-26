---
description: This Interface Represents a Collection of Region Rects.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalRegionRectCollectionView
ms.date: 02/26/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalRegionRectCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalRegionRectCollectionView
- ICoreWebView2ExperimentalRegionRectCollectionView.get_Count
- ICoreWebView2ExperimentalRegionRectCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalRegionRectCollectionView

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalRegionRectCollectionView
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Count

This method gets the number of Rects contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

This method gets the Rect at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, RECT * value)

