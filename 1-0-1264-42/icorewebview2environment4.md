---
description: A continuation of the ICoreWebView2Environment3 interface.
title: WebView2 Win32 C++ ICoreWebView2Environment4
ms.date: 06/29/2022
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
[GetAutomationProviderForWindow](#getautomationproviderforwindow) | Returns the Automation Provider for the WebView that matches the provided window.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### GetAutomationProviderForWindow

Returns the Automation Provider for the WebView that matches the provided window.

> public HRESULT [GetAutomationProviderForWindow](#getautomationproviderforwindow)(HWND hwnd, IUnknown ** provider)

Host apps are expected to implement IRawElementProviderHwndOverride. When GetOverrideProviderForHwnd is called, the app can pass the HWND to GetAutomationProviderForWindow to find the matching WebView Automation Provider.

