---
description: Receives `BasicAuthenticationRequested` events.
title: WebView2 Win32 C++ ICoreWebView2BasicAuthenticationRequestedEventHandler
ms.date: 10/29/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BasicAuthenticationRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2BasicAuthenticationRequestedEventHandler
- ICoreWebView2BasicAuthenticationRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BasicAuthenticationRequestedEventHandler

```
interface ICoreWebView2BasicAuthenticationRequestedEventHandler
  : public IUnknown
```

Receives `BasicAuthenticationRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2BasicAuthenticationRequestedEventArgs](icorewebview2basicauthenticationrequestedeventargs.md#icorewebview2basicauthenticationrequestedeventargs) * args)

