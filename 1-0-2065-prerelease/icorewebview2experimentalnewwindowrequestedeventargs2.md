---
description: This is a continuation of the ICoreWebView2NewWindowRequestedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalNewWindowRequestedEventArgs2
ms.date: 08/28/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalNewWindowRequestedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalNewWindowRequestedEventArgs2
- ICoreWebView2ExperimentalNewWindowRequestedEventArgs2.get_OriginalSourceFrameInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalNewWindowRequestedEventArgs2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalNewWindowRequestedEventArgs2
  : public IUnknown
```

This is a continuation of the [ICoreWebView2NewWindowRequestedEventArgs](icorewebview2newwindowrequestedeventargs.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_OriginalSourceFrameInfo](#get_originalsourceframeinfo) | The frame info of the frame where the new window request originated.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_OriginalSourceFrameInfo

The frame info of the frame where the new window request originated.

> public HRESULT [get_OriginalSourceFrameInfo](#get_originalsourceframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md) ** frameInfo)

The `OriginalSourceFrameInfo` is a snapshot of frame information at the time when the new window was requested. See [ICoreWebView2FrameInfo](icorewebview2frameinfo.md) for details on frame properties.

