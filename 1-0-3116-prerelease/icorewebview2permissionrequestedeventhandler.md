---
description: Receives `PermissionRequested` events.
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventHandler
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2PermissionRequestedEventHandler
- ICoreWebView2PermissionRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PermissionRequestedEventHandler

```
interface ICoreWebView2PermissionRequestedEventHandler
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
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2PermissionRequestedEventArgs](icorewebview2permissionrequestedeventargs.md#icorewebview2permissionrequestedeventargs) * args)

