---
description: This interface is used to complete deferrals on event args that support getting deferrals via their GetDeferral method.
title: WebView2 Win32 C++ ICoreWebView2Deferral
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/07/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Deferral
---

# interface ICoreWebView2Deferral 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Deferral
  : public IUnknown
```

This interface is used to complete deferrals on event args that support getting deferrals via their GetDeferral method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Complete](#complete) | Completes the associated deferred event.

## Members

#### Complete 

Completes the associated deferred event.

> public HRESULT [Complete](#complete)()

Complete should only be called once for each deferral taken.

