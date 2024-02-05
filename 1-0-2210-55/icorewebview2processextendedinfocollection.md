---
description: A list containing processInfo and associated extended information.
title: WebView2 Win32 C++ ICoreWebView2ProcessExtendedInfoCollection
ms.date: 01/29/2024
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

A list containing processInfo and associated extended information.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of process contained in the ICoreWebView2ProcessExtendedInfoCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the [ICoreWebView2ProcessExtendedInfo](icorewebview2processextendedinfo.md) located in the ICoreWebView2ProcessExtendedInfoCollection at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Count

The number of process contained in the ICoreWebView2ProcessExtendedInfoCollection.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the [ICoreWebView2ProcessExtendedInfo](icorewebview2processextendedinfo.md) located in the ICoreWebView2ProcessExtendedInfoCollection at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ProcessExtendedInfo](icorewebview2processextendedinfo.md) ** processInfo)

