---
description: Receives `WebTextureStreamStopped` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler
ms.date: 07/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler
- ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamWebTextureStreamStoppedEventHandler
  : public IUnknown
```

Receives `WebTextureStreamStopped` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) * sender, IUnknown * args)

