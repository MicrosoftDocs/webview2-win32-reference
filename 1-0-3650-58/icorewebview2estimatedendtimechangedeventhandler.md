---
description: Receives `EstimatedEndTimeChanged` events.
title: WebView2 Win32 C++ ICoreWebView2EstimatedEndTimeChangedEventHandler
ms.date: 12/02/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EstimatedEndTimeChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2EstimatedEndTimeChangedEventHandler
- ICoreWebView2EstimatedEndTimeChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EstimatedEndTimeChangedEventHandler

```
interface ICoreWebView2EstimatedEndTimeChangedEventHandler
  : public IUnknown
```

Receives `EstimatedEndTimeChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2DownloadOperation](icorewebview2downloadoperation.md#icorewebview2downloadoperation) * sender, IUnknown * args)

