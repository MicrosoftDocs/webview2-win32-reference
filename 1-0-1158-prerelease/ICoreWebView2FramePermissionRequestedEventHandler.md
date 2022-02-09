---
description: Receives `PermissionRequested` events.
title: WebView2 Win32 C++ ICoreWebView2FramePermissionRequestedEventHandler
ms.date: 02/08/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FramePermissionRequestedEventHandler
---

# interface ICoreWebView2FramePermissionRequestedEventHandler

```
interface ICoreWebView2FramePermissionRequestedEventHandler
  : public IUnknown
```

Receives `PermissionRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](ICoreWebView2Frame.md) * sender,[ICoreWebView2PermissionRequestedEventArgs2](ICoreWebView2PermissionRequestedEventArgs2.md) * args)

