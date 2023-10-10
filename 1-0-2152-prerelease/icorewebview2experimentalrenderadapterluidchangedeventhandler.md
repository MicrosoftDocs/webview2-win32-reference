---
description: This is the callback for the browser process's display LUID change.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalRenderAdapterLUIDChangedEventHandler
ms.date: 10/10/2023
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

This is the callback for the browser process's display LUID change.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### Invoke

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalEnvironment12](icorewebview2experimentalenvironment12.md) * sender, IUnknown * args)

