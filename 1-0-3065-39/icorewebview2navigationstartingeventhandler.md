---
description: Receives `NavigationStarting` events.
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventHandler
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationStartingEventHandler
- ICoreWebView2NavigationStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NavigationStartingEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NavigationStartingEventHandler
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
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2NavigationStartingEventArgs](icorewebview2navigationstartingeventargs.md#icorewebview2navigationstartingeventargs) * args)

