---
description: This is the ICoreWebView2 Experimental interface to support FrameCreated event.
title: WebView2 Win32 C++ ICoreWebView2Experimental
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental
---

# interface ICoreWebView2Experimental

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental
  : public IUnknown
```

This is the ICoreWebView2 Experimental interface to support FrameCreated event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_FrameCreated](#add_framecreated) | Raised when a new iframe is created.
[remove_FrameCreated](#remove_framecreated) | Remove an event handler previously added with add_FrameCreated.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.579

## Members

#### add_FrameCreated

Raised when a new iframe is created.

> public HRESULT [add_FrameCreated](#add_framecreated)(ICoreWebView2ExperimentalFrameCreatedEventHandler * eventHandler, EventRegistrationToken * token)

Use the CoreWebView2Frame.add_Destroyed to listen for when this iframe goes away.

#### remove_FrameCreated

Remove an event handler previously added with add_FrameCreated.

> public HRESULT [remove_FrameCreated](#remove_framecreated)(EventRegistrationToken token)

