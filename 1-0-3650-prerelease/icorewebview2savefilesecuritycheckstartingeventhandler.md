---
description: Receives `SaveFileSecurityCheckStarting` events.
title: WebView2 Win32 C++ ICoreWebView2SaveFileSecurityCheckStartingEventHandler
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SaveFileSecurityCheckStartingEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2SaveFileSecurityCheckStartingEventHandler
- ICoreWebView2SaveFileSecurityCheckStartingEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SaveFileSecurityCheckStartingEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2SaveFileSecurityCheckStartingEventHandler
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
WebView2 Win32            |    1.0.2849.39
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, [ICoreWebView2SaveFileSecurityCheckStartingEventArgs](icorewebview2savefilesecuritycheckstartingeventargs.md#icorewebview2savefilesecuritycheckstartingeventargs) * args)

