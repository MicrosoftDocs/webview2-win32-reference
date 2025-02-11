---
description: Receives `ProcessInfosChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ProcessInfosChangedEventHandler
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessInfosChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessInfosChangedEventHandler
- ICoreWebView2ProcessInfosChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessInfosChangedEventHandler

```
interface ICoreWebView2ProcessInfosChangedEventHandler
  : public IUnknown
```

Receives `ProcessInfosChanged` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) * sender, IUnknown * args)

