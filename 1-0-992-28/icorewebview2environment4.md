---
description: A continuation of the ICoreWebView2Environment3 interface.
title: WebView2 Win32 C++ ICoreWebView2Environment4
ms.date: 09/27/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment4
---

# interface ICoreWebView2Environment4

```
interface ICoreWebView2Environment4
  : public ICoreWebView2Environment3
```

A continuation of the [ICoreWebView2Environment3](icorewebview2environment3.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetProviderForHwnd](#getproviderforhwnd) | Returns the UI Automation Provider for the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) that corresponds with the given HWND.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### GetProviderForHwnd

Returns the UI Automation Provider for the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md) that corresponds with the given HWND.

> public HRESULT [GetProviderForHwnd](#getproviderforhwnd)(HWND hwnd, IUnknown ** provider)

