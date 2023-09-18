---
description: 
title: WebView2 Win32 C++ ICoreWebView2ProcessFailedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessFailedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessFailedEventArgs
- ICoreWebView2ProcessFailedEventArgs.get_ProcessFailedKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessFailedEventArgs

```
interface ICoreWebView2ProcessFailedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ProcessFailedKind](#get_processfailedkind) | Gets the `ProcessFailedKind` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_ProcessFailedKind

Gets the `ProcessFailedKind` property.

> public HRESULT [get_ProcessFailedKind](#get_processfailedkind)(COREWEBVIEW2_PROCESS_FAILED_KIND * value)

