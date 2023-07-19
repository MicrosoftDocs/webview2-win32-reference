---
description: This is the ICoreWebView2ExperimentalFrameInfo that provides `ParentFrameInfo`, `FrameId` and `FrameKind` properties.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrameInfo
ms.date: 07/19/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrameInfo
---

# interface ICoreWebView2ExperimentalFrameInfo

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrameInfo
  : public IUnknown
```

This is the ICoreWebView2ExperimentalFrameInfo that provides `ParentFrameInfo`, `FrameId` and `FrameKind` properties.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FrameId](#get_frameid) | The unique identifier of the frame associated with the current `FrameInfo`.
[get_FrameKind](#get_framekind) | The frame kind of the frame.
[get_ParentFrameInfo](#get_parentframeinfo) | This frame's parent frame's `FrameInfo`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_FrameId

The unique identifier of the frame associated with the current `FrameInfo`.

> public HRESULT [get_FrameId](#get_frameid)(UINT32 * id)

It's the same kind of ID as with the `FrameId` in `CoreWebView2` and via `CoreWebView2Frame`. `FrameId` will only be populated when obtained calling `CoreWebView2ProcessInfo.AssociatedFrameInfos`. `CoreWebView2FrameInfo` objects obtained via `CoreWebView2.ProcessFailed` will always have an invalid frame Id 0. Note that this `FrameId` could be out of date as it's a snapshot.

#### get_FrameKind

The frame kind of the frame.

> public HRESULT [get_FrameKind](#get_framekind)(COREWEBVIEW2_FRAME_KIND * kind)

`FrameKind` will only be populated when obtained calling `CoreWebView2ProcessInfo.AssociatedFrameInfos`. `CoreWebView2FrameInfo` objects obtained via `CoreWebView2.ProcessFailed` will always have the default value `COREWEBVIEW2_FRAME_KIND_OTHER`. Note that this `FrameKind` could be out of date as it's a snapshot.

#### get_ParentFrameInfo

This frame's parent frame's `FrameInfo`.

> public HRESULT [get_ParentFrameInfo](#get_parentframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md) ** frameInfo)

`ParentFrameInfo` will only be populated when obtained via calling `CoreWebView2ProcessInfo.AssociatedFrameInfos`. `CoreWebView2FrameInfo` objects obtained via `CoreWebView2.ProcessFailed` will always have a `null``ParentFrameInfo`. This property is also `null` for the top most document in the WebView2 which has no parent frame. Note that this `ParentFrameInfo` could be out of date as it's a snapshot.

