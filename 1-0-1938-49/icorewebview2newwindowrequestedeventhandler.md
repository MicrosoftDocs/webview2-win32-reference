---
description: Receives `NewWindowRequested` events.
title: WebView2 Win32 C++ ICoreWebView2NewWindowRequestedEventHandler
ms.date: 08/21/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewWindowRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2NewWindowRequestedEventHandler
- ICoreWebView2NewWindowRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NewWindowRequestedEventHandler

```
interface ICoreWebView2NewWindowRequestedEventHandler
  : public IUnknown
```

Receives `NewWindowRequested` events.

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

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2NewWindowRequestedEventArgs * args)

