---
description: A collection of ICoreWebView2ExperimentalSensitivityLabel.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSensitivityLabelCollectionView
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSensitivityLabelCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSensitivityLabelCollectionView
- ICoreWebView2ExperimentalSensitivityLabelCollectionView.get_Count
- ICoreWebView2ExperimentalSensitivityLabelCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSensitivityLabelCollectionView

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSensitivityLabelCollectionView
  : public IUnknown
```

A collection of [ICoreWebView2ExperimentalSensitivityLabel](icorewebview2experimentalsensitivitylabel.md#icorewebview2experimentalsensitivitylabel).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalSensitivityLabel](icorewebview2experimentalsensitivitylabel.md#icorewebview2experimentalsensitivitylabel) ** value)

