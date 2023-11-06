---
description: A list containing processInfo and associated extended information.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessExtendedInfoCollection
ms.date: 11/06/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessExtendedInfoCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProcessExtendedInfoCollection
- ICoreWebView2ExperimentalProcessExtendedInfoCollection.get_Count
- ICoreWebView2ExperimentalProcessExtendedInfoCollection.GetValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProcessExtendedInfoCollection

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessExtendedInfoCollection
  : public IUnknown
```

A list containing processInfo and associated extended information.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of process contained in the `ICoreWebView2ProcessExtendedInfoCollection`.
[GetValueAtIndex](#getvalueatindex) | Gets the [ICoreWebView2ExperimentalProcessExtendedInfo](icorewebview2experimentalprocessextendedinfo.md) located in the ICoreWebView2ExperimentalProcessExtendedInfoCollection at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2106

## Members

#### get_Count

The number of process contained in the `ICoreWebView2ProcessExtendedInfoCollection`.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the [ICoreWebView2ExperimentalProcessExtendedInfo](icorewebview2experimentalprocessextendedinfo.md) located in the ICoreWebView2ExperimentalProcessExtendedInfoCollection at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalProcessExtendedInfo](icorewebview2experimentalprocessextendedinfo.md) ** processInfo)

