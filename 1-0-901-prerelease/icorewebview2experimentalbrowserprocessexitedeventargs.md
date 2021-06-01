---
description: Event args for the `BrowserProcessExited` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBrowserProcessExitedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/01/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBrowserProcessExitedEventArgs
---

# interface ICoreWebView2ExperimentalBrowserProcessExitedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBrowserProcessExitedEventArgs
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.901

## Members

#### get_BrowserProcessExitKind

The kind of browser process exit that has occurred.

> public HRESULT [get_BrowserProcessExitKind](#get_browserprocessexitkind)(COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND * browserProcessExitKind)

#### get_BrowserProcessId

The process ID of the browser process that has exited.

> public HRESULT [get_BrowserProcessId](#get_browserprocessid)(UINT32 * value)

