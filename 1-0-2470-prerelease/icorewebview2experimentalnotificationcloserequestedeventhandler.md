---
description: An event handler for the `CloseRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler
- ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNotificationCloseRequestedEventHandler
  : public IUnknown
```

An event handler for the `CloseRequested` event.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalNotification](icorewebview2experimentalnotification.md#icorewebview2experimentalnotification) * sender, IUnknown * args)

