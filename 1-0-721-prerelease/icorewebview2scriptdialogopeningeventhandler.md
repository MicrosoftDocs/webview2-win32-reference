---
description: Receives `ScriptDialogOpening` events.
title: WebView2 Win32 C++ ICoreWebView2ScriptDialogOpeningEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/08/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ScriptDialogOpeningEventHandler
---

# interface ICoreWebView2ScriptDialogOpeningEventHandler 

```
interface ICoreWebView2ScriptDialogOpeningEventHandler
  : public IUnknown
```

Receives `ScriptDialogOpening` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Members

#### Invoke 

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2ScriptDialogOpeningEventArgs](icorewebview2scriptdialogopeningeventargs.md) * args)

