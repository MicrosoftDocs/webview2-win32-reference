---
description: This interface is an extension of the ICoreWebView2Environment that supports creating print settings for printing to PDF.
title: WebView2 Win32 C++ ICoreWebView2Environment6
ms.date: 05/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment6
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment6
- ICoreWebView2Environment6.CreatePrintSettings
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment6

```
interface ICoreWebView2Environment6
  : public ICoreWebView2Environment5
```

This interface is an extension of the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) that supports creating print settings for printing to PDF.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreatePrintSettings](#createprintsettings) | Creates the [ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) used by the `PrintToPdf` method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1020.30
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### CreatePrintSettings

Creates the [ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) used by the `PrintToPdf` method.

> public HRESULT [CreatePrintSettings](#createprintsettings)([ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) ** value)

