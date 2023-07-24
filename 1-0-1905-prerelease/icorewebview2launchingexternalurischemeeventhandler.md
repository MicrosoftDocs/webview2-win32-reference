---
description: Event handler for the `LaunchingExternalUriScheme` event.
title: WebView2 Win32 C++ ICoreWebView2LaunchingExternalUriSchemeEventHandler
ms.date: 07/24/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2LaunchingExternalUriSchemeEventHandler
---

# interface ICoreWebView2LaunchingExternalUriSchemeEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2LaunchingExternalUriSchemeEventHandler
  : public IUnknown
```

Event handler for the `LaunchingExternalUriScheme` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Receives the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Receives the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2LaunchingExternalUriSchemeEventArgs * args)

