---
description: Receives `ActiveMatchIndexChanged` events.
title: WebView2 Win32 C++ ICoreWebView2FindActiveMatchIndexChangedEventHandler
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FindActiveMatchIndexChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FindActiveMatchIndexChangedEventHandler
- ICoreWebView2FindActiveMatchIndexChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FindActiveMatchIndexChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2FindActiveMatchIndexChangedEventHandler
  : public IUnknown
```

Receives `ActiveMatchIndexChanged` events.

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

