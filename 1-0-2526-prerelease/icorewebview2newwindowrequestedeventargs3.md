---
description: This is a continuation of the ICoreWebView2NewWindowRequestedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2NewWindowRequestedEventArgs3
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewWindowRequestedEventArgs3
topic_type: 
- APIRef
api_name:
- ICoreWebView2NewWindowRequestedEventArgs3
- ICoreWebView2NewWindowRequestedEventArgs3.get_OriginalSourceFrameInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NewWindowRequestedEventArgs3

```
interface ICoreWebView2NewWindowRequestedEventArgs3
  : public ICoreWebView2NewWindowRequestedEventArgs2
```

This is a continuation of the [ICoreWebView2NewWindowRequestedEventArgs](icorewebview2newwindowrequestedeventargs.md#icorewebview2newwindowrequestedeventargs) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_OriginalSourceFrameInfo](#get_originalsourceframeinfo) | The frame info of the frame where the new window request originated.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2151.40
WebView2 Win32 Prerelease |    1.0.2106

## Members

#### get_OriginalSourceFrameInfo

The frame info of the frame where the new window request originated.

> public HRESULT [get_OriginalSourceFrameInfo](#get_originalsourceframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) ** frameInfo)

The `OriginalSourceFrameInfo` is a snapshot of frame information at the time when the new window was requested. See [ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) for details on frame properties.

