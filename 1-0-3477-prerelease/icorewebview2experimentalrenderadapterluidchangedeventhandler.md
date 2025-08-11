---
description: Receives `RenderAdapterLUIDChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler
- ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler
  : public IUnknown
```

Receives `RenderAdapterLUIDChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalEnvironment12](icorewebview2experimentalenvironment12.md#icorewebview2experimentalenvironment12) * sender, IUnknown * args)

