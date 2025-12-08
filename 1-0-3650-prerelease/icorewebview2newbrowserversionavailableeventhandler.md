---
description: Receives `NewBrowserVersionAvailable` events.
title: WebView2 Win32 C++ ICoreWebView2NewBrowserVersionAvailableEventHandler
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewBrowserVersionAvailableEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NewBrowserVersionAvailableEventHandler
- ICoreWebView2NewBrowserVersionAvailableEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NewBrowserVersionAvailableEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NewBrowserVersionAvailableEventHandler
  : public IUnknown
```

Receives `NewBrowserVersionAvailable` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) * sender, IUnknown * args)

