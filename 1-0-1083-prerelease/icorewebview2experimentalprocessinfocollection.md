---
description: A list containing process id and corresponding process type.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessInfoCollection
ms.date: 11/29/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessInfoCollection
---

# interface ICoreWebView2ExperimentalProcessInfoCollection

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessInfoCollection
  : public IUnknown
```

A list containing process id and corresponding process type.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of process contained in the ICoreWebView2ExperimentalProcessInfoCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the ICoreWebView2ExperimentalProcessInfo located in the ICoreWebView2ExperimentalProcessInfoCollection at the given index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### get_Count

The number of process contained in the ICoreWebView2ExperimentalProcessInfoCollection.

> public HRESULT [get_Count](#get_count)(UINT * count)

#### GetValueAtIndex

Gets the ICoreWebView2ExperimentalProcessInfo located in the ICoreWebView2ExperimentalProcessInfoCollection at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, ICoreWebView2ExperimentalProcessInfo ** processInfo)

