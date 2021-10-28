---
description: The caller implements this interface to handle the BasicAuthenticationRequested event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalBasicAuthenticationRequestedEventHandler
ms.date: 10/28/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalBasicAuthenticationRequestedEventHandler
---

# interface ICoreWebView2ExperimentalBasicAuthenticationRequestedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalBasicAuthenticationRequestedEventHandler
  : public IUnknown
```

The caller implements this interface to handle the BasicAuthenticationRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### Invoke

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, [ICoreWebView2ExperimentalBasicAuthenticationRequestedEventArgs](icorewebview2experimentalbasicauthenticationrequestedeventargs.md) * args)

