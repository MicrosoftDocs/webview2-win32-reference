---
description: This interface is an extension of ICoreWebView2_5 that manages opening the browser task manager window.
title: WebView2 Win32 C++ ICoreWebView2_6
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_6
topic_type: 
- APIRef
api_name:
- ICoreWebView2_6
- ICoreWebView2_6.OpenTaskManagerWindow
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_6

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_6
  : public ICoreWebView2_5
```

This interface is an extension of [ICoreWebView2_5](icorewebview2_5.md#icorewebview2_5) that manages opening the browser task manager window.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[OpenTaskManagerWindow](#opentaskmanagerwindow) | Opens the Browser Task Manager view as a new window in the foreground.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### OpenTaskManagerWindow

Opens the Browser Task Manager view as a new window in the foreground.

> public HRESULT [OpenTaskManagerWindow](#opentaskmanagerwindow)()

If the Browser Task Manager is already open, this will bring it into the foreground. WebView2 currently blocks the Shift+Esc shortcut for opening the task manager. An end user can open the browser task manager manually via the `Browser task manager` entry of the DevTools window's title bar's context menu.

