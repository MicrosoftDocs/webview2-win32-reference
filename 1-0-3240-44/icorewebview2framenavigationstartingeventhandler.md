---
description: Receives `NavigationStarting` events.
title: WebView2 Win32 C++ ICoreWebView2FrameNavigationStartingEventHandler
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameNavigationStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameNavigationStartingEventHandler
- ICoreWebView2FrameNavigationStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameNavigationStartingEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2FrameNavigationStartingEventHandler
  : public IUnknown
```

Receives `NavigationStarting` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2NavigationStartingEventArgs](icorewebview2navigationstartingeventargs.md#icorewebview2navigationstartingeventargs) * args)

