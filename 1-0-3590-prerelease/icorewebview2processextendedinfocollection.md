---
description: A collection of ICoreWebView2ProcessExtendedInfo.
title: WebView2 Win32 C++ ICoreWebView2ProcessExtendedInfoCollection
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessExtendedInfoCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessExtendedInfoCollection
- ICoreWebView2ProcessExtendedInfoCollection.get_Count
- ICoreWebView2ProcessExtendedInfoCollection.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessExtendedInfoCollection

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProcessExtendedInfoCollection
  : public IUnknown
```

A collection of [ICoreWebView2ProcessExtendedInfo](icorewebview2processextendedinfo.md#icorewebview2processextendedinfo).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of elements contained in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the element at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_Count

The number of elements contained in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the element at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ProcessExtendedInfo](icorewebview2processextendedinfo.md#icorewebview2processextendedinfo) ** value)

