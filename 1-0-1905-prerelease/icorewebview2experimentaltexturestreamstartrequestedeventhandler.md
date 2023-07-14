---
description: This is the callback for new texture stream request.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler
ms.date: 07/14/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler
[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]
- ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler
api_type:
- COM
---

# interface ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler

```
interface ICoreWebView2ExperimentalTextureStreamStartRequestedEventHandler
  : public IUnknown
```

This is the callback for new texture stream request.

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

> public HRESULT [Invoke](#invoke)(ICoreWebView2ExperimentalTextureStream * sender, IUnknown * args)

There are no event args and the args parameter will be null.

