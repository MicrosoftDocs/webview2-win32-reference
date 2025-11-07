---
description: Receives `RestartRequested` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalRestartRequestedEventHandler
ms.date: 10/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalRestartRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalRestartRequestedEventHandler
- ICoreWebView2ExperimentalRestartRequestedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalRestartRequestedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalRestartRequestedEventHandler
  : public IUnknown
```

Receives `RestartRequested` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment) * sender, [ICoreWebView2ExperimentalRestartRequestedEventArgs](icorewebview2experimentalrestartrequestedeventargs.md#icorewebview2experimentalrestartrequestedeventargs) * args)

