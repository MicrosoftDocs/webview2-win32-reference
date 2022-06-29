---
description: Receives `ContextMenuRequested` events.
title: WebView2 Win32 C++ ICoreWebView2ContextMenuRequestedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuRequestedEventHandler
---

# interface ICoreWebView2ContextMenuRequestedEventHandler

```
interface ICoreWebView2ContextMenuRequestedEventHandler
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
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### Invoke

Called to provide the event args when a context menu is requested on a WebView element.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2ContextMenuRequestedEventArgs * args)

