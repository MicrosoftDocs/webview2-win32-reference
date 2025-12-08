---
description: Receives `MatchCountChanged` events.
title: WebView2 Win32 C++ ICoreWebView2FindMatchCountChangedEventHandler
ms.date: 12/02/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FindMatchCountChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FindMatchCountChangedEventHandler
- ICoreWebView2FindMatchCountChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FindMatchCountChangedEventHandler

```
interface ICoreWebView2FindMatchCountChangedEventHandler
  : public IUnknown
```

Receives `MatchCountChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3405.78
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Find](icorewebview2find.md#icorewebview2find) * sender, IUnknown * args)

