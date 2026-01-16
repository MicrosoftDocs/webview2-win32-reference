---
description: Receives `SensitivityInfoChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler
- ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSensitivityInfoChangedEventHandler
  : public IUnknown
```

Receives `SensitivityInfoChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, IUnknown * args)

