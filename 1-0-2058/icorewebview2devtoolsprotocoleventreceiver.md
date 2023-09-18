---
description: 
title: WebView2 Win32 C++ ICoreWebView2DevToolsProtocolEventReceiver
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DevToolsProtocolEventReceiver
topic_type: 
- APIRef
api_name:
- ICoreWebView2DevToolsProtocolEventReceiver
- ICoreWebView2DevToolsProtocolEventReceiver.add_DevToolsProtocolEventReceived
- ICoreWebView2DevToolsProtocolEventReceiver.remove_DevToolsProtocolEventReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DevToolsProtocolEventReceiver

```
interface ICoreWebView2DevToolsProtocolEventReceiver
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DevToolsProtocolEventReceived](#add_devtoolsprotocoleventreceived) | Adds an event handler for the `DevToolsProtocolEventReceived` event.
[remove_DevToolsProtocolEventReceived](#remove_devtoolsprotocoleventreceived) | Removes an event handler previously added with `add_DevToolsProtocolEventReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_DevToolsProtocolEventReceived

Adds an event handler for the `DevToolsProtocolEventReceived` event.

> public HRESULT [add_DevToolsProtocolEventReceived](#add_devtoolsprotocoleventreceived)([ICoreWebView2DevToolsProtocolEventReceivedEventHandler](icorewebview2devtoolsprotocoleventreceivedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### remove_DevToolsProtocolEventReceived

Removes an event handler previously added with `add_DevToolsProtocolEventReceived`.

> public HRESULT [remove_DevToolsProtocolEventReceived](#remove_devtoolsprotocoleventreceived)(EventRegistrationToken token)

