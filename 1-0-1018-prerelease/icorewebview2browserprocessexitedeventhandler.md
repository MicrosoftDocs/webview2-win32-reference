---
description: Receives `BrowserProcessExited` events.
title: WebView2 Win32 C++ ICoreWebView2BrowserProcessExitedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserProcessExitedEventHandler
---

# interface ICoreWebView2BrowserProcessExitedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Environment](icorewebview2environment.md) * sender, [ICoreWebView2BrowserProcessExitedEventArgs](icorewebview2browserprocessexitedeventargs.md) * args)

