---
description: Event args for the `BrowserProcessExited` event.
title: WebView2 Win32 C++ ICoreWebView2BrowserProcessExitedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserProcessExitedEventArgs
---

# interface ICoreWebView2BrowserProcessExitedEventArgs

```
interface ICoreWebView2BrowserProcessExitedEventArgs
  : public IUnknown
```

Event args for the `BrowserProcessExited` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_BrowserProcessExitKind](#get_browserprocessexitkind) | The kind of browser process exit that has occurred.
[get_BrowserProcessId](#get_browserprocessid) | The process ID of the browser process that has exited.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_BrowserProcessExitKind

The kind of browser process exit that has occurred.

> public HRESULT [get_BrowserProcessExitKind](#get_browserprocessexitkind)(COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND * browserProcessExitKind)

#### get_BrowserProcessId

The process ID of the browser process that has exited.

> public HRESULT [get_BrowserProcessId](#get_browserprocessid)(UINT32 * value)

