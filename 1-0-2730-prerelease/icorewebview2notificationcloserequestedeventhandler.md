---
description: Receives `CloseRequested` events.
title: WebView2 Win32 C++ ICoreWebView2NotificationCloseRequestedEventHandler
ms.date: 07/31/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NotificationCloseRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NotificationCloseRequestedEventHandler
- ICoreWebView2NotificationCloseRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NotificationCloseRequestedEventHandler

```
interface ICoreWebView2NotificationCloseRequestedEventHandler
  : public IUnknown
```

Receives `CloseRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Notification](icorewebview2notification.md#icorewebview2notification) * sender, IUnknown * args)

