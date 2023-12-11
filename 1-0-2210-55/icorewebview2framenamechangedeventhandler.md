---
description: Receives `FrameNameChanged` event.
title: WebView2 Win32 C++ ICoreWebView2FrameNameChangedEventHandler
ms.date: 12/11/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameNameChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameNameChangedEventHandler
- ICoreWebView2FrameNameChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameNameChangedEventHandler

```
interface ICoreWebView2FrameNameChangedEventHandler
  : public IUnknown
```

Receives `FrameNameChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result for the iframe name changed event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### Invoke

Provides the result for the iframe name changed event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2Frame * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

