---
description: Receives the result of the `GetProcessInfosWithDetails` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler
ms.date: 07/25/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler
- ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetProcessInfosWithDetailsCompletedHandler
  : public IUnknown
```

Receives the result of the `GetProcessInfosWithDetails` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the process info list for the `GetProcessInfosWithDetails`.

The result is written to the collection of `ProcessInfo`s provided in the `GetProcessInfosWithDetails` method call.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### Invoke

Provides the process info list for the `GetProcessInfosWithDetails`.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ProcessInfoCollection](icorewebview2processinfocollection.md) * value)

