---
description: This is an extension of the ICoreWebView2Frame interface that surfaces the `LaunchingExternalUriScheme` event at the iframe level.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrame10
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrame10
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrame10
- ICoreWebView2ExperimentalFrame10.add_LaunchingExternalUriScheme
- ICoreWebView2ExperimentalFrame10.remove_LaunchingExternalUriScheme
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrame10

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrame10
  : public IUnknown
```

This is an extension of the [ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) interface that surfaces the `LaunchingExternalUriScheme` event at the iframe level.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_LaunchingExternalUriScheme](#add_launchingexternalurischeme) | Adds an event handler for the `LaunchingExternalUriScheme` event.
[remove_LaunchingExternalUriScheme](#remove_launchingexternalurischeme) | Removes an event handler previously added with `add_LaunchingExternalUriScheme`.

Host apps can subscribe per-iframe to attribute external URI scheme launches to a specific iframe even when multiple frames share the same origin.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### add_LaunchingExternalUriScheme

Adds an event handler for the `LaunchingExternalUriScheme` event.

> public HRESULT [add_LaunchingExternalUriScheme](#add_launchingexternalurischeme)([ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler](icorewebview2experimentalframelaunchingexternalurischemeeventhandler.md#icorewebview2experimentalframelaunchingexternalurischemeeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `LaunchingExternalUriScheme` event. `LaunchingExternalUriScheme` is raised when content in this `CoreWebView2Frame`, or in one of its descendant iframes, attempts to launch a URI registered with the OS as an external scheme handler. When the launch originates from a nested iframe, the event bubbles outward through the tracked `CoreWebView2Frame` ancestors, starting with the closest (innermost) tracked frame and proceeding outward toward the top-level frame.

This relates to the `LaunchingExternalUriScheme` event on the `CoreWebView2`. For an iframe-initiated launch the `CoreWebView2Frame`'s event handlers are invoked before the `CoreWebView2`'s event handlers. If the `Handled` property of the event args is set to `TRUE` within a `CoreWebView2Frame` event handler, then the event will not be raised on the remaining ancestor frames or on the `CoreWebView2`, and their event handlers will not be invoked.

If a deferral is not taken on the event args, the external URI scheme launch is blocked until the event handler returns. If a deferral is taken, the launch is blocked until the deferral is completed. To suppress the `CoreWebView2`-level event handlers, `Handled` must be set synchronously before any deferral is taken.

#### remove_LaunchingExternalUriScheme

Removes an event handler previously added with `add_LaunchingExternalUriScheme`.

> public HRESULT [remove_LaunchingExternalUriScheme](#remove_launchingexternalurischeme)(EventRegistrationToken token)

