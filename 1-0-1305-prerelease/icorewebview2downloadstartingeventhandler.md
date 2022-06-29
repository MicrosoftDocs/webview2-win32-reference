---
description: Add an event handler for the `DownloadStarting` event.
title: WebView2 Win32 C++ ICoreWebView2DownloadStartingEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DownloadStartingEventHandler
---

# interface ICoreWebView2DownloadStartingEventHandler

```
interface ICoreWebView2DownloadStartingEventHandler
  : public IUnknown
```

Add an event handler for the `DownloadStarting` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2DownloadStartingEventArgs * args)

