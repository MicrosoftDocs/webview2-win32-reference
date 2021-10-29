---
description: Receives `ContextMenuRequested` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalContextMenuRequestedEventHandler
ms.date: 10/28/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalContextMenuRequestedEventHandler
---

# interface ICoreWebView2ExperimentalContextMenuRequestedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalContextMenuRequestedEventHandler
  : public IUnknown
```

Receives `ContextMenuRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the event args when a context menu is requested on a WebView element.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Called to provide the event args when a context menu is requested on a WebView element.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2ExperimentalContextMenuRequestedEventArgs](icorewebview2experimentalcontextmenurequestedeventargs.md) * args)

