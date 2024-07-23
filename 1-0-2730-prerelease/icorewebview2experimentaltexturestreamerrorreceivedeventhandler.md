---
description: Receives `ErrorReceived` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
ms.date: 07/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
- ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
  : public IUnknown
```

Receives `ErrorReceived` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) * sender, [ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs](icorewebview2experimentaltexturestreamerrorreceivedeventargs.md#icorewebview2experimentaltexturestreamerrorreceivedeventargs) * args)

