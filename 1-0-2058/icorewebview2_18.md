---
description: 
title: WebView2 Win32 C++ ICoreWebView2_18
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_18
topic_type: 
- APIRef
api_name:
- ICoreWebView2_18
- ICoreWebView2_18.add_LaunchingExternalUriScheme
- ICoreWebView2_18.remove_LaunchingExternalUriScheme
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_18

```
interface ICoreWebView2_18
  : public ICoreWebView2_17
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_LaunchingExternalUriScheme](#add_launchingexternalurischeme) | Adds an event handler for the `LaunchingExternalUriScheme` event.
[remove_LaunchingExternalUriScheme](#remove_launchingexternalurischeme) | Removes an event handler previously added with `add_LaunchingExternalUriScheme`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### add_LaunchingExternalUriScheme

Adds an event handler for the `LaunchingExternalUriScheme` event.

> public HRESULT [add_LaunchingExternalUriScheme](#add_launchingexternalurischeme)([ICoreWebView2LaunchingExternalUriSchemeEventHandler](icorewebview2launchingexternalurischemeeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_LaunchingExternalUriScheme

Removes an event handler previously added with `add_LaunchingExternalUriScheme`.

> public HRESULT [remove_LaunchingExternalUriScheme](#remove_launchingexternalurischeme)(EventRegistrationToken token)

