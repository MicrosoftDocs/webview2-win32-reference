---
description: A continuation of the ICoreWebView2FrameInfo interface that provides `ParentFrameInfo`, `FrameId` and `FrameKind` properties.
title: WebView2 Win32 C++ ICoreWebView2FrameInfo2
ms.date: 10/27/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameInfo2
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameInfo2
- ICoreWebView2FrameInfo2.get_FrameId
- ICoreWebView2FrameInfo2.get_FrameKind
- ICoreWebView2FrameInfo2.get_ParentFrameInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameInfo2

```
interface ICoreWebView2FrameInfo2
  : public ICoreWebView2FrameInfo
```

A continuation of the [ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) interface that provides `ParentFrameInfo`, `FrameId` and `FrameKind` properties.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FrameId](#get_frameid) | The unique identifier of the frame associated with the current `FrameInfo`.
[get_FrameKind](#get_framekind) | The frame kind of the frame.
[get_ParentFrameInfo](#get_parentframeinfo) | This parent frame's `FrameInfo`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_FrameId

The unique identifier of the frame associated with the current `FrameInfo`.

> public HRESULT [get_FrameId](#get_frameid)(UINT32 * id)

It's the same kind of ID as with the `FrameId` in `CoreWebView2` and via `CoreWebView2Frame`. `FrameId` will only be populated (non-zero) when obtained calling `CoreWebView2ProcessExtendedInfo.AssociatedFrameInfos`. `CoreWebView2FrameInfo` objects obtained via `CoreWebView2.ProcessFailed` will always have an invalid frame Id 0. Note that this `FrameId` could be out of date as it's a snapshot. If there's WebView2 created or destroyed or `FrameCreated/FrameDestroyed` events after the asynchronous call `CoreWebView2Environment.GetProcessExtendedInfos` starts, you may want to call asynchronous method again to get the updated `FrameInfo`s.

#### get_FrameKind

The frame kind of the frame.

> public HRESULT [get_FrameKind](#get_framekind)(COREWEBVIEW2_FRAME_KIND * kind)

`FrameKind` will only be populated when obtained calling `CoreWebView2ProcessExtendedInfo.AssociatedFrameInfos`. `CoreWebView2FrameInfo` objects obtained via `CoreWebView2.ProcessFailed` will always have the default value `COREWEBVIEW2_FRAME_KIND_UNKNOWN`. Note that this `FrameKind` could be out of date as it's a snapshot.

#### get_ParentFrameInfo

This parent frame's `FrameInfo`.

> public HRESULT [get_ParentFrameInfo](#get_parentframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) ** frameInfo)

`ParentFrameInfo` will only be populated when obtained via calling `CoreWebView2ProcessExtendedInfo.AssociatedFrameInfos`. `CoreWebView2FrameInfo` objects obtained via `CoreWebView2.ProcessFailed` will always have a `null ParentFrameInfo`. This property is also `null` for the main frame in the WebView2 which has no parent frame. Note that this `ParentFrameInfo` could be out of date as it's a snapshot.

