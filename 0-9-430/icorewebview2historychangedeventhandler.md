---
description: The caller implements this interface to receive the HistoryChanged event.
title: WebView2 Win32 C++ ICoreWebView2HistoryChangedEventHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Host, browser control, edge html
---

# interface ICoreWebView2HistoryChangedEventHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2HistoryChangedEventHandler
  : public IUnknown
```

The caller implements this interface to receive the HistoryChanged event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | There are no event args and the args parameter will be null.

## Members

#### Invoke 

There are no event args and the args parameter will be null.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](ICoreWebView2.md) * webview,IUnknown * args)

