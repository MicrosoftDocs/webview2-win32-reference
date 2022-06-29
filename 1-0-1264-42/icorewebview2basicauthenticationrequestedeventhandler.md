---
description: The caller implements this interface to handle the BasicAuthenticationRequested event.
title: WebView2 Win32 C++ ICoreWebView2BasicAuthenticationRequestedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BasicAuthenticationRequestedEventHandler
---

# interface ICoreWebView2BasicAuthenticationRequestedEventHandler

```
interface ICoreWebView2BasicAuthenticationRequestedEventHandler
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
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### Invoke

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2BasicAuthenticationRequestedEventArgs * args)

