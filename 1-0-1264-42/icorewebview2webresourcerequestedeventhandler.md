---
description: Runs when a URL request (through network, file, and so on) is made in the webview for a Web resource matching resource context filter and URL specified in `AddWebResourceRequestedFilter`.
title: WebView2 Win32 C++ ICoreWebView2WebResourceRequestedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceRequestedEventHandler
---

# interface ICoreWebView2WebResourceRequestedEventHandler

```
interface ICoreWebView2WebResourceRequestedEventHandler
  : public IUnknown
```

Runs when a URL request (through network, file, and so on) is made in the webview for a Web resource matching resource context filter and URL specified in `AddWebResourceRequestedFilter`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

The host views and modifies the request or provide a response in a similar pattern to HTTP, in which case the request immediately completed. This may not contain any request headers that are added by the network stack, such as an `Authorization` header.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, ICoreWebView2WebResourceRequestedEventArgs * args)

