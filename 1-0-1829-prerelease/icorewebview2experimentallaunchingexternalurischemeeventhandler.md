---
description: Event handler for the `LaunchingExternalUriScheme` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventHandler
ms.date: 05/02/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventHandler
---

# interface ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### Invoke

Receives the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs](icorewebview2experimentallaunchingexternalurischemeeventargs.md) * args)

