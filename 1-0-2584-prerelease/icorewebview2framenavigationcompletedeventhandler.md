---
description: Receives `NavigationCompleted` events for iframe.
title: WebView2 Win32 C++ ICoreWebView2FrameNavigationCompletedEventHandler
ms.date: 05/13/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameNavigationCompletedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameNavigationCompletedEventHandler
- ICoreWebView2FrameNavigationCompletedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameNavigationCompletedEventHandler

```
interface ICoreWebView2FrameNavigationCompletedEventHandler
  : public IUnknown
```

Receives `NavigationCompleted` events for iframe.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2NavigationCompletedEventArgs](icorewebview2navigationcompletedeventargs.md#icorewebview2navigationcompletedeventargs) * args)

