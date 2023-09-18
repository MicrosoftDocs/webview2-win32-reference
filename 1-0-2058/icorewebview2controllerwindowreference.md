---
description: 
title: WebView2 Win32 C++ ICoreWebView2ControllerWindowReference
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerWindowReference
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerWindowReference
- ICoreWebView2ControllerWindowReference.get_CoreWindow
- ICoreWebView2ControllerWindowReference.get_WindowHandle
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerWindowReference

```
interface ICoreWebView2ControllerWindowReference
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CoreWindow](#get_corewindow) | Gets the `CoreWindow` property.
[get_WindowHandle](#get_windowhandle) | Gets the `WindowHandle` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_CoreWindow

Gets the `CoreWindow` property.

> public HRESULT [get_CoreWindow](#get_corewindow)(Windows.UI.Core.CoreWindow ** value)

#### get_WindowHandle

Gets the `WindowHandle` property.

> public HRESULT [get_WindowHandle](#get_windowhandle)(UINT64 * value)

