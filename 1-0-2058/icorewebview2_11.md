---
description: 
title: WebView2 Win32 C++ ICoreWebView2_11
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_11
topic_type: 
- APIRef
api_name:
- ICoreWebView2_11
- ICoreWebView2_11.add_ContextMenuRequested
- ICoreWebView2_11.CallDevToolsProtocolMethodForSession
- ICoreWebView2_11.remove_ContextMenuRequested
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_11

```
interface ICoreWebView2_11
  : public ICoreWebView2_10
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ContextMenuRequested](#add_contextmenurequested) | Adds an event handler for the `ContextMenuRequested` event.
[CallDevToolsProtocolMethodForSession](#calldevtoolsprotocolmethodforsession) | 
[remove_ContextMenuRequested](#remove_contextmenurequested) | Removes an event handler previously added with `add_ContextMenuRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### add_ContextMenuRequested

Adds an event handler for the `ContextMenuRequested` event.

> public HRESULT [add_ContextMenuRequested](#add_contextmenurequested)([ICoreWebView2ContextMenuRequestedEventHandler](icorewebview2contextmenurequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### CallDevToolsProtocolMethodForSession

> public HRESULT [CallDevToolsProtocolMethodForSession](#calldevtoolsprotocolmethodforsession)(LPCWSTR sessionId, LPCWSTR methodName, LPCWSTR parametersAsJson, [ICoreWebView2CallDevToolsProtocolMethodCompletedHandler](icorewebview2calldevtoolsprotocolmethodcompletedhandler.md) * handler)

#### remove_ContextMenuRequested

Removes an event handler previously added with `add_ContextMenuRequested`.

> public HRESULT [remove_ContextMenuRequested](#remove_contextmenurequested)(EventRegistrationToken token)

