---
description: Receives `BrowserProcessExited` events.
title: WebView2 Win32 C++ ICoreWebView2BrowserProcessExitedEventHandler
ms.date: 04/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserProcessExitedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2BrowserProcessExitedEventHandler
- ICoreWebView2BrowserProcessExitedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BrowserProcessExitedEventHandler

```
interface ICoreWebView2BrowserProcessExitedEventHandler
  : public IUnknown
```

Receives `BrowserProcessExited` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) * sender, [ICoreWebView2BrowserProcessExitedEventArgs](icorewebview2browserprocessexitedeventargs.md#icorewebview2browserprocessexitedeventargs) * args)

