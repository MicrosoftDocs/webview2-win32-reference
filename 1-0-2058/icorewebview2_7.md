---
description: 
title: WebView2 Win32 C++ ICoreWebView2_7
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_7
topic_type: 
- APIRef
api_name:
- ICoreWebView2_7
- ICoreWebView2_7.PrintToPdf
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_7

```
interface ICoreWebView2_7
  : public ICoreWebView2_6
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PrintToPdf](#printtopdf) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1020.30
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### PrintToPdf

> public HRESULT [PrintToPdf](#printtopdf)(LPCWSTR ResultFilePath, [ICoreWebView2PrintSettings](icorewebview2printsettings.md) * printSettings, [ICoreWebView2PrintToPdfCompletedHandler](icorewebview2printtopdfcompletedhandler.md) * handler)

