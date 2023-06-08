---
description: This is the callback for texture stream rendering error.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
ms.date: 06/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
---

# interface ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalTextureStreamErrorReceivedEventHandler
  : public IUnknown
```

This is the callback for texture stream rendering error.

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

> public HRESULT [Invoke](#invoke)(ICoreWebView2ExperimentalTextureStream * sender, ICoreWebView2ExperimentalTextureStreamErrorReceivedEventArgs * args)

