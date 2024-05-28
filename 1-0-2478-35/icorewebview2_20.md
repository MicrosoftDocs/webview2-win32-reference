---
description: This interface is an extension of ICoreWebView2_19 that provides the `FrameId` property.
title: WebView2 Win32 C++ ICoreWebView2_20
ms.date: 05/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_20
topic_type: 
- APIRef
api_name:
- ICoreWebView2_20
- ICoreWebView2_20.get_FrameId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_20

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_20
  : public ICoreWebView2_19
```

This interface is an extension of [ICoreWebView2_19](icorewebview2_19.md#icorewebview2_19) that provides the `FrameId` property.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FrameId](#get_frameid) | The unique identifier of the main frame.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_FrameId

The unique identifier of the main frame.

> public HRESULT [get_FrameId](#get_frameid)(UINT32 * id)

It's the same kind of ID as with the `FrameId` in `CoreWebView2Frame` and via `CoreWebView2FrameInfo`. Note that `FrameId` may not be valid if `CoreWebView2` has not done any navigation. It's safe to get this value during or after the first `ContentLoading` event. Otherwise, it could return the invalid frame Id 0.

