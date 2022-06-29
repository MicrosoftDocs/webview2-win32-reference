---
description: Receives `FrameCreated` event.
title: WebView2 Win32 C++ ICoreWebView2FrameCreatedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameCreatedEventHandler
---

# interface ICoreWebView2FrameCreatedEventHandler

```
interface ICoreWebView2FrameCreatedEventHandler
  : public IUnknown
```

Receives `FrameCreated` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result for the iframe created event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the result for the iframe created event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2FrameCreatedEventArgs](icorewebview2framecreatedeventargs.md) * args)

