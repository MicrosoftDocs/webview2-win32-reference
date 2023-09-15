---
description: 
title: WebView2 Win32 C++ ICoreWebView2BrowserProcessExitedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserProcessExitedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2BrowserProcessExitedEventArgs
- ICoreWebView2BrowserProcessExitedEventArgs.get_BrowserProcessExitKind
- ICoreWebView2BrowserProcessExitedEventArgs.get_BrowserProcessId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BrowserProcessExitedEventArgs

```
interface ICoreWebView2BrowserProcessExitedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_BrowserProcessExitKind](#get_browserprocessexitkind) | Gets the `BrowserProcessExitKind` property.
[get_BrowserProcessId](#get_browserprocessid) | Gets the `BrowserProcessId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_BrowserProcessExitKind

Gets the `BrowserProcessExitKind` property.

> public HRESULT [get_BrowserProcessExitKind](#get_browserprocessexitkind)(COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND * value)

#### get_BrowserProcessId

Gets the `BrowserProcessId` property.

> public HRESULT [get_BrowserProcessId](#get_browserprocessid)(UINT32 * value)

