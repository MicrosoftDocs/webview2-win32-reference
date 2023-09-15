---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment5
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment5
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment5
- ICoreWebView2Environment5.add_BrowserProcessExited
- ICoreWebView2Environment5.remove_BrowserProcessExited
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment5

```
interface ICoreWebView2Environment5
  : public ICoreWebView2Environment4
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BrowserProcessExited](#add_browserprocessexited) | Adds an event handler for the `BrowserProcessExited` event.
[remove_BrowserProcessExited](#remove_browserprocessexited) | Removes an event handler previously added with `add_BrowserProcessExited`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### add_BrowserProcessExited

Adds an event handler for the `BrowserProcessExited` event.

> public HRESULT [add_BrowserProcessExited](#add_browserprocessexited)([ICoreWebView2BrowserProcessExitedEventHandler](icorewebview2browserprocessexitedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_BrowserProcessExited

Removes an event handler previously added with `add_BrowserProcessExited`.

> public HRESULT [remove_BrowserProcessExited](#remove_browserprocessexited)(EventRegistrationToken token)

