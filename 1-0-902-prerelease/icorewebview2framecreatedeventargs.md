---
description: Event args for the `FrameCreated` events.
title: WebView2 Win32 C++ ICoreWebView2FrameCreatedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/03/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameCreatedEventArgs
---

# interface ICoreWebView2FrameCreatedEventArgs

```
interface ICoreWebView2FrameCreatedEventArgs
  : public IUnknown
```

Event args for the `FrameCreated` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Frame](#get_frame) | The frame which was created.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_Frame

The frame which was created.

> public HRESULT [get_Frame](#get_frame)([ICoreWebView2Frame](icorewebview2frame.md) ** frame)

