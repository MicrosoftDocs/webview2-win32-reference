---
description: Event args for the `FrameCreated` events.
title: WebView2 Win32 C++ ICoreWebView2FrameCreatedEventArgs
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameCreatedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameCreatedEventArgs
- ICoreWebView2FrameCreatedEventArgs.get_Frame
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameCreatedEventArgs

```
interface ICoreWebView2FrameCreatedEventArgs
  : public IUnknown
```

Event args for the `FrameCreated` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Frame](#get_frame) | The frame which was created.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_Frame

The frame which was created.

> public HRESULT [get_Frame](#get_frame)([ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) ** value)

