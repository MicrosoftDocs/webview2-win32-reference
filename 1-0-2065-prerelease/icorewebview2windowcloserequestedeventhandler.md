---
description: Receives `WindowCloseRequested` events.
title: WebView2 Win32 C++ ICoreWebView2WindowCloseRequestedEventHandler
ms.date: 09/20/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WindowCloseRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2WindowCloseRequestedEventHandler
- ICoreWebView2WindowCloseRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WindowCloseRequestedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2WindowCloseRequestedEventHandler
  : public IUnknown
```

Receives `WindowCloseRequested` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

