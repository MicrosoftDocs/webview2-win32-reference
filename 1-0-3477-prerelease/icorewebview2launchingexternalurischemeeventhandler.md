---
description: Receives `LaunchingExternalUriScheme` events.
title: WebView2 Win32 C++ ICoreWebView2LaunchingExternalUriSchemeEventHandler
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2LaunchingExternalUriSchemeEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2LaunchingExternalUriSchemeEventHandler
- ICoreWebView2LaunchingExternalUriSchemeEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2LaunchingExternalUriSchemeEventHandler

```
interface ICoreWebView2LaunchingExternalUriSchemeEventHandler
  : public IUnknown
```

Receives `LaunchingExternalUriScheme` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2LaunchingExternalUriSchemeEventArgs](icorewebview2launchingexternalurischemeeventargs.md#icorewebview2launchingexternalurischemeeventargs) * args)

