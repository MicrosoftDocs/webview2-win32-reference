---
description: This is the ICoreWebView2_24 interface that manages WebView2 Web Notification functionality.
title: WebView2 Win32 C++ ICoreWebView2_24
ms.date: 01/16/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_24
topic_type: 
- APIRef
api_name:
- ICoreWebView2_24
- ICoreWebView2_24.add_NotificationReceived
- ICoreWebView2_24.remove_NotificationReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_24

```
interface ICoreWebView2_24
  : public ICoreWebView2_23
```

This is the ICoreWebView2_24 interface that manages WebView2 Web Notification functionality.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_NotificationReceived](#add_notificationreceived) | Adds an event handler for the `NotificationReceived` event.
[remove_NotificationReceived](#remove_notificationreceived) | Removes an event handler previously added with `add_NotificationReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2739.15
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### add_NotificationReceived

Adds an event handler for the `NotificationReceived` event.

> public HRESULT [add_NotificationReceived](#add_notificationreceived)([ICoreWebView2NotificationReceivedEventHandler](icorewebview2notificationreceivedeventhandler.md#icorewebview2notificationreceivedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `NotificationReceived` event for non-persistent notifications.

If a deferral is not taken on the event args, the subsequent scripts after the DOM notification creation call (i.e. `Notification()`) are blocked until the event handler returns. If a deferral is taken, the scripts are blocked until the deferral is completed.

#### remove_NotificationReceived

Removes an event handler previously added with `add_NotificationReceived`.

> public HRESULT [remove_NotificationReceived](#remove_notificationreceived)(EventRegistrationToken token)

