---
description: This is the ICoreWebView2ExperimentalFrame5 that provides the `FrameId` property.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrame5
ms.date: 10/16/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrame5
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrame5
- ICoreWebView2ExperimentalFrame5.get_FrameId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrame5

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrame5
  : public IUnknown
```

This is the ICoreWebView2ExperimentalFrame5 that provides the `FrameId` property.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FrameId](#get_frameid) | The unique identifier of the current frame.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### get_FrameId

The unique identifier of the current frame.

> public HRESULT [get_FrameId](#get_frameid)(UINT32 * id)

It's the same kind of ID as with the `FrameId` in `CoreWebView2` and via `CoreWebView2FrameInfo`.

