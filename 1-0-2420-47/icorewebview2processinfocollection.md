---
description: A list containing process id and corresponding process type.
title: WebView2 Win32 C++ ICoreWebView2ProcessInfoCollection
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessInfoCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessInfoCollection
- ICoreWebView2ProcessInfoCollection.get_Count
- ICoreWebView2ProcessInfoCollection.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessInfoCollection

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProcessInfoCollection
  : public IUnknown
```

A list containing process id and corresponding process type.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of process contained in the ICoreWebView2ProcessInfoCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the [ICoreWebView2ProcessInfo](icorewebview2processinfo.md#icorewebview2processinfo) located in the ICoreWebView2ProcessInfoCollection at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_Count

The number of process contained in the ICoreWebView2ProcessInfoCollection.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the [ICoreWebView2ProcessInfo](icorewebview2processinfo.md#icorewebview2processinfo) located in the ICoreWebView2ProcessInfoCollection at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ProcessInfo](icorewebview2processinfo.md#icorewebview2processinfo) ** processInfo)

