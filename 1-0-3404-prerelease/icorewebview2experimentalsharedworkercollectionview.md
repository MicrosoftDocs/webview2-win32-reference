---
description: A collection of ICoreWebView2ExperimentalSharedWorker.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSharedWorkerCollectionView
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSharedWorkerCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSharedWorkerCollectionView
- ICoreWebView2ExperimentalSharedWorkerCollectionView.get_Count
- ICoreWebView2ExperimentalSharedWorkerCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSharedWorkerCollectionView

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSharedWorkerCollectionView
  : public IUnknown
```

A collection of [ICoreWebView2ExperimentalSharedWorker](icorewebview2experimentalsharedworker.md#icorewebview2experimentalsharedworker).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalSharedWorker](icorewebview2experimentalsharedworker.md#icorewebview2experimentalsharedworker) ** value)

