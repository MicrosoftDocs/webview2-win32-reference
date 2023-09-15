---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment11
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment11
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment11
- ICoreWebView2Environment11.get_FailureReportFolderPath
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment11

```
interface ICoreWebView2Environment11
  : public ICoreWebView2Environment10
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FailureReportFolderPath](#get_failurereportfolderpath) | Gets the `FailureReportFolderPath` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### get_FailureReportFolderPath

Gets the `FailureReportFolderPath` property.

> public HRESULT [get_FailureReportFolderPath](#get_failurereportfolderpath)(LPWSTR * value)

