---
description: Receives `ActiveMatchIndexChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler
- ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFindActiveMatchIndexChangedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3079

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalFind](icorewebview2experimentalfind.md#icorewebview2experimentalfind) * sender, IUnknown * args)

