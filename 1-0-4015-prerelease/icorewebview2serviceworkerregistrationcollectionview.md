---
description: A collection of ICoreWebView2ServiceWorkerRegistration.
title: WebView2 Win32 C++ ICoreWebView2ServiceWorkerRegistrationCollectionView
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ServiceWorkerRegistrationCollectionView
topic_type: 
- APIRef
api_name:
- ICoreWebView2ServiceWorkerRegistrationCollectionView
- ICoreWebView2ServiceWorkerRegistrationCollectionView.get_Count
- ICoreWebView2ServiceWorkerRegistrationCollectionView.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ServiceWorkerRegistrationCollectionView

```
interface ICoreWebView2ServiceWorkerRegistrationCollectionView
  : public IUnknown
```

A collection of [ICoreWebView2ServiceWorkerRegistration](icorewebview2serviceworkerregistration.md#icorewebview2serviceworkerregistration).

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

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ServiceWorkerRegistration](icorewebview2serviceworkerregistration.md#icorewebview2serviceworkerregistration) ** value)

