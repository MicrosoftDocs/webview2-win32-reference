---
description: This is the ICoreWebView2Experimental22 interface that manages WebView2 Web Notification functionality.
title: WebView2 Win32 C++ ICoreWebView2Experimental22
ms.date: 02/26/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental22
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental22
- ICoreWebView2Experimental22.add_NotificationReceived
- ICoreWebView2Experimental22.remove_NotificationReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental22

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental22
  : public IUnknown
```

This is the ICoreWebView2Experimental22 interface that manages WebView2 Web Notification functionality.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_NotificationReceived](#add_notificationreceived) | Add an event handler for the `NotificationReceived` event for non-persistent notifications.
[remove_NotificationReceived](#remove_notificationreceived) | Remove an event handler previously added with `add_NotificationReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### add_NotificationReceived

Add an event handler for the `NotificationReceived` event for non-persistent notifications.

> public HRESULT [add_NotificationReceived](#add_notificationreceived)([ICoreWebView2ExperimentalNotificationReceivedEventHandler](icorewebview2experimentalnotificationreceivedeventhandler.md) * eventHandler, EventRegistrationToken * token)

If a deferral is not taken on the event args, the subsequent scripts after the DOM notification creation call (i.e. `Notification()`) are blocked until the event handler returns. If a deferral is taken, the scripts are blocked until the deferral is completed.

#### remove_NotificationReceived

Remove an event handler previously added with `add_NotificationReceived`.

> public HRESULT [remove_NotificationReceived](#remove_notificationreceived)(EventRegistrationToken token)

