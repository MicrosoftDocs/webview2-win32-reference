---
description: A collection of ICoreWebView2SharedWorker.
title: WebView2 Win32 C++ ICoreWebView2SharedWorkerCollectionView
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SharedWorkerCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2SharedWorkerCollectionView
- ICoreWebView2SharedWorkerCollectionView.get_Count
- ICoreWebView2SharedWorkerCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SharedWorkerCollectionView

```
interface ICoreWebView2SharedWorkerCollectionView
  : public IUnknown
```

A collection of [ICoreWebView2SharedWorker](icorewebview2sharedworker.md#icorewebview2sharedworker).

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

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2SharedWorker](icorewebview2sharedworker.md#icorewebview2sharedworker) ** value)

