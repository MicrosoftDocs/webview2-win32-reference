---
description: This interface is an extension of ICoreWebView2 that manages opening the browser task manager window.
title: WebView2 Win32 C++ ICoreWebView2Experimental4
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental4
---

# interface ICoreWebView2Experimental4

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental4
  : public IUnknown
```

This interface is an extension of ICoreWebView2 that manages opening the browser task manager window.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[OpenTaskManagerWindow](#opentaskmanagerwindow) | Opens the Browser Task Manager view as a new window.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.955

## Members

#### OpenTaskManagerWindow

Opens the Browser Task Manager view as a new window.

> public HRESULT [OpenTaskManagerWindow](#opentaskmanagerwindow)()

Does nothing when the Browser Task Manager is already open. WebView2 currently blocks the `Shift+Esc` shortcut for opening the task manager. An end user can open the browser task manager manually via the `Browser task manager` entry of the DevTools window's title bar's context menu.

