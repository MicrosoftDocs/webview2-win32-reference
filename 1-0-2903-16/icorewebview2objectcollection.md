---
description: Represents a collection of generic objects.
title: WebView2 Win32 C++ ICoreWebView2ObjectCollection
ms.date: 10/29/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ObjectCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2ObjectCollection
- ICoreWebView2ObjectCollection.InsertValueAtIndex
- ICoreWebView2ObjectCollection.RemoveValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ObjectCollection

```
interface ICoreWebView2ObjectCollection
  : public ICoreWebView2ObjectCollectionView
```

Represents a collection of generic objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[InsertValueAtIndex](#insertvalueatindex) | Inserts the object at the specified index.
[RemoveValueAtIndex](#removevalueatindex) | Removes the object at the specified index.

Used to get, remove and add objects at the specified index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2651.64
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### InsertValueAtIndex

Inserts the object at the specified index.

> public HRESULT [InsertValueAtIndex](#insertvalueatindex)(UINT32 index, IUnknown * value)

#### RemoveValueAtIndex

Removes the object at the specified index.

> public HRESULT [RemoveValueAtIndex](#removevalueatindex)(UINT32 index)

