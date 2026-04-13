---
description: A collection of origin settings.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalOriginFeatureSettingCollectionView
ms.date: 04/08/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalOriginFeatureSettingCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalOriginFeatureSettingCollectionView
- ICoreWebView2ExperimentalOriginFeatureSettingCollectionView.get_Count
- ICoreWebView2ExperimentalOriginFeatureSettingCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalOriginFeatureSettingCollectionView

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalOriginFeatureSettingCollectionView
  : public IUnknown
```

A collection of origin settings.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | Gets the number of objects contained in the `OriginFeatureSettingCollection`.
[GetValueAtIndex](#getvalueatindex) | Gets the object at the specified index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Count

Gets the number of objects contained in the `OriginFeatureSettingCollection`.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the object at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalOriginFeatureSetting](icorewebview2experimentaloriginfeaturesetting.md#icorewebview2experimentaloriginfeaturesetting) ** value)

