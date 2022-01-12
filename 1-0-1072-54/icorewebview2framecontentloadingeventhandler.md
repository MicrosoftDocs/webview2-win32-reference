---
description: Receives `ContentLoading` events for iframe.
title: WebView2 Win32 C++ ICoreWebView2FrameContentLoadingEventHandler
ms.date: 01/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameContentLoadingEventHandler
---

# interface ICoreWebView2FrameContentLoadingEventHandler

```
interface ICoreWebView2FrameContentLoadingEventHandler
  : public IUnknown
```

Receives `ContentLoading` events for iframe.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md) * sender, [ICoreWebView2ContentLoadingEventArgs](icorewebview2contentloadingeventargs.md) * args)

