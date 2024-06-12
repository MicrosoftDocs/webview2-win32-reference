---
description: Receives `NotificationReceived` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNotificationReceivedEventHandler
ms.date: 06/12/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNotificationReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalNotificationReceivedEventHandler
- ICoreWebView2ExperimentalNotificationReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalNotificationReceivedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNotificationReceivedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ExperimentalNotificationReceivedEventArgs](icorewebview2experimentalnotificationreceivedeventargs.md#icorewebview2experimentalnotificationreceivedeventargs) * args)

