---
description: This is the callback for stop request of texture stream.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamStoppedEventHandler
ms.date: 04/10/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamStoppedEventHandler
---

# interface ICoreWebView2ExperimentalTextureStreamStoppedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamStoppedEventHandler
  : public IUnknown
```

This is the callback for stop request of texture stream.

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

