---
description: Event args for the `RestartRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalRestartRequestedEventArgs
ms.date: 05/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalRestartRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalRestartRequestedEventArgs
- ICoreWebView2ExperimentalRestartRequestedEventArgs.get_Priority
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalRestartRequestedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalRestartRequestedEventArgs
  : public IUnknown
```

Event args for the `RestartRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Priority](#get_priority) | Restart requested priority.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### get_Priority

Restart requested priority.

> public HRESULT [get_Priority](#get_priority)(COREWEBVIEW2_RESTART_REQUESTED_PRIORITY * value)

