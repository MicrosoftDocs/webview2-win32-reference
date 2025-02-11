---
description: Receives `NavigationCompleted` events.
title: WebView2 Win32 C++ ICoreWebView2NavigationCompletedEventHandler
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationCompletedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationCompletedEventHandler
- ICoreWebView2NavigationCompletedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NavigationCompletedEventHandler

```
interface ICoreWebView2NavigationCompletedEventHandler
  : public IUnknown
```

Receives `NavigationCompleted` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2NavigationCompletedEventArgs](icorewebview2navigationcompletedeventargs.md#icorewebview2navigationcompletedeventargs) * args)

