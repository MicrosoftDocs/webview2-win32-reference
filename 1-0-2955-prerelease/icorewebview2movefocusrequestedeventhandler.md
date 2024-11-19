---
description: Receives `MoveFocusRequested` events.
title: WebView2 Win32 C++ ICoreWebView2MoveFocusRequestedEventHandler
ms.date: 11/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2MoveFocusRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2MoveFocusRequestedEventHandler
- ICoreWebView2MoveFocusRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2MoveFocusRequestedEventHandler

```
interface ICoreWebView2MoveFocusRequestedEventHandler
  : public IUnknown
```

Receives `MoveFocusRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Controller](icorewebview2controller.md#icorewebview2controller) * sender, [ICoreWebView2MoveFocusRequestedEventArgs](icorewebview2movefocusrequestedeventargs.md#icorewebview2movefocusrequestedeventargs) * args)

