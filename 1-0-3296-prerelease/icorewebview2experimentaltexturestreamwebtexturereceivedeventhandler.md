---
description: Receives `WebTextureReceived` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler
- ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventHandler
  : public IUnknown
```

Receives `WebTextureReceived` events.

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

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) * sender, [ICoreWebView2ExperimentalTextureStreamWebTextureReceivedEventArgs](icorewebview2experimentaltexturestreamwebtexturereceivedeventargs.md#icorewebview2experimentaltexturestreamwebtexturereceivedeventargs) * args)

