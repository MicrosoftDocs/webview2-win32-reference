---
description: Receives `StatusBarTextChanged` events.
title: WebView2 Win32 C++ ICoreWebView2StatusBarTextChangedEventHandler
ms.date: 10/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2StatusBarTextChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2StatusBarTextChangedEventHandler
- ICoreWebView2StatusBarTextChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2StatusBarTextChangedEventHandler

```
interface ICoreWebView2StatusBarTextChangedEventHandler
  : public IUnknown
```

Receives `StatusBarTextChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, IUnknown * args)

