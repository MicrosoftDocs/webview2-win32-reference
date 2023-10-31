---
description: Raised to notify the host that the end user selected a custom `ContextMenuItem`.
title: WebView2 Win32 C++ ICoreWebView2CustomItemSelectedEventHandler
ms.date: 10/31/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CustomItemSelectedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2CustomItemSelectedEventHandler
- ICoreWebView2CustomItemSelectedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CustomItemSelectedEventHandler

```
interface ICoreWebView2CustomItemSelectedEventHandler
  : public IUnknown
```

Raised to notify the host that the end user selected a custom `ContextMenuItem`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

`CustomItemSelected` event is raised on the specific `ContextMenuItem` that the end user selected.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

