---
description: Receives `NotificationReceived` events.
title: WebView2 Win32 C++ ICoreWebView2NotificationReceivedEventHandler
ms.date: 01/13/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NotificationReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NotificationReceivedEventHandler
- ICoreWebView2NotificationReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NotificationReceivedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NotificationReceivedEventHandler
  : public IUnknown
```

Receives `NotificationReceived` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2739.15
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2NotificationReceivedEventArgs](icorewebview2notificationreceivedeventargs.md#icorewebview2notificationreceivedeventargs) * args)

