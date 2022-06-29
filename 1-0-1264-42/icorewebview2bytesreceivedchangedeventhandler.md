---
description: Implements the interface to receive `BytesReceivedChanged` event.
title: WebView2 Win32 C++ ICoreWebView2BytesReceivedChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BytesReceivedChangedEventHandler
---

# interface ICoreWebView2BytesReceivedChangedEventHandler

```
interface ICoreWebView2BytesReceivedChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `BytesReceivedChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the `ICoreWebView2DownloadOperation.BytesReceived` property to get the received bytes count.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2DownloadOperation * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

