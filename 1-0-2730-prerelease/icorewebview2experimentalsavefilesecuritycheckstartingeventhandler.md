---
description: Receives `SaveFileSecurityCheckStarting` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventHandler
ms.date: 08/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventHandler
- ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventHandler
  : public IUnknown
```

Receives `SaveFileSecurityCheckStarting` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2ExperimentalSaveFileSecurityCheckStartingEventArgs](icorewebview2experimentalsavefilesecuritycheckstartingeventargs.md#icorewebview2experimentalsavefilesecuritycheckstartingeventargs) * args)

