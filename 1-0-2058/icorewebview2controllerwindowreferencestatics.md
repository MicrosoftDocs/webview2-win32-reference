---
description: 
title: WebView2 Win32 C++ ICoreWebView2ControllerWindowReferenceStatics
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerWindowReferenceStatics
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerWindowReferenceStatics
- ICoreWebView2ControllerWindowReferenceStatics.CreateFromCoreWindow
- ICoreWebView2ControllerWindowReferenceStatics.CreateFromWindowHandle
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerWindowReferenceStatics

```
interface ICoreWebView2ControllerWindowReferenceStatics
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateFromCoreWindow](#createfromcorewindow) | 
[CreateFromWindowHandle](#createfromwindowhandle) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### CreateFromCoreWindow

> public HRESULT [CreateFromCoreWindow](#createfromcorewindow)(Windows.UI.Core.CoreWindow * coreWindow, HWND ** value)

#### CreateFromWindowHandle

> public HRESULT [CreateFromWindowHandle](#createfromwindowhandle)(UINT64 windowHandle, HWND ** value)

