---
description: A list containing process id and corresponding process type.
title: WebView2 Win32 C++ ICoreWebView2ProcessInfoCollection
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessInfoCollection
---

# interface ICoreWebView2ProcessInfoCollection

```
interface ICoreWebView2ProcessInfoCollection
  : public IUnknown
```

A list containing process id and corresponding process type.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of process contained in the ICoreWebView2ProcessInfoCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the ICoreWebView2ProcessInfo located in the ICoreWebView2ProcessInfoCollection at the given index.

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

Gets the ICoreWebView2ProcessInfo located in the ICoreWebView2ProcessInfoCollection at the given index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, ICoreWebView2ProcessInfo ** processInfo)

