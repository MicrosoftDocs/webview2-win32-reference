---
description: Receives `LaunchingExternalUriScheme` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler
- ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameLaunchingExternalUriSchemeEventHandler
  : public IUnknown
```

Receives `LaunchingExternalUriScheme` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) * sender, [ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2](icorewebview2experimentallaunchingexternalurischemeeventargs2.md#icorewebview2experimentallaunchingexternalurischemeeventargs2) * args)

