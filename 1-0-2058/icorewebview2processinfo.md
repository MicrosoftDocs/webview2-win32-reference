---
description: 
title: WebView2 Win32 C++ ICoreWebView2ProcessInfo
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessInfo
- ICoreWebView2ProcessInfo.get_Kind
- ICoreWebView2ProcessInfo.get_ProcessId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessInfo

```
interface ICoreWebView2ProcessInfo
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Kind](#get_kind) | Gets the `Kind` property.
[get_ProcessId](#get_processid) | Gets the `ProcessId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_Kind

Gets the `Kind` property.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_PROCESS_KIND * value)

#### get_ProcessId

Gets the `ProcessId` property.

> public HRESULT [get_ProcessId](#get_processid)(INT32 * value)

