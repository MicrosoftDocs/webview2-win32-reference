---
description: A collection of ICoreWebView2ExperimentalServiceWorkerRegistration.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView
ms.date: 07/08/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView
- ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView.get_Count
- ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerRegistrationCollectionView
  : public IUnknown
```

A collection of [ICoreWebView2ExperimentalServiceWorkerRegistration](icorewebview2experimentalserviceworkerregistration.md#icorewebview2experimentalserviceworkerregistration).

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

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalServiceWorkerRegistration](icorewebview2experimentalserviceworkerregistration.md#icorewebview2experimentalserviceworkerregistration) ** value)

