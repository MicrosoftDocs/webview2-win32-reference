---
description: Receives `DownloadStarting` events.
title: WebView2 Win32 C++ ICoreWebView2DownloadStartingEventHandler
ms.date: 05/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DownloadStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2DownloadStartingEventHandler
- ICoreWebView2DownloadStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DownloadStartingEventHandler

```
interface ICoreWebView2DownloadStartingEventHandler
  : public IUnknown
```

Receives `DownloadStarting` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2DownloadStartingEventArgs](icorewebview2downloadstartingeventargs.md#icorewebview2downloadstartingeventargs) * args)

