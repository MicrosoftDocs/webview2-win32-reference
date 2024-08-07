---
description: Event args for the `ScreenCaptureStarting` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalScreenCaptureStartingEventArgs
ms.date: 07/31/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalScreenCaptureStartingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs.get_Cancel
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs.get_Handled
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs.get_OriginalSourceFrameInfo
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs.GetDeferral
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs.put_Cancel
- ICoreWebView2ExperimentalScreenCaptureStartingEventArgs.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalScreenCaptureStartingEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalScreenCaptureStartingEventArgs
  : public IUnknown
```

Event args for the `ScreenCaptureStarting` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_OriginalSourceFrameInfo](#get_originalsourceframeinfo) | The associated frame information that requests the screen capture permission.
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_Cancel](#put_cancel) | The host may set this flag to cancel the screen capture.
[put_Handled](#put_handled) | By default, both the `ScreenCaptureStarting` event handlers on the `CoreWebView2Frame` and the `CoreWebView2` will be invoked, with the `CoreWebView2Frame` event handlers invoked first.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### get_Cancel

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_OriginalSourceFrameInfo

The associated frame information that requests the screen capture permission.

> public HRESULT [get_OriginalSourceFrameInfo](#get_originalsourceframeinfo)([ICoreWebView2FrameInfo](icorewebview2frameinfo.md#icorewebview2frameinfo) ** value)

This can be used to get the frame source, name, frameId, and parent frame information.

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** value)

Use this deferral to defer the decision to show the Screen Capture UI. getDisplayMedia() won't call its callbacks until the deferral is completed.

#### put_Cancel

The host may set this flag to cancel the screen capture.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

If canceled, the screen capture UI is not displayed regardless of the `Handled` property. On the script side, it will return with a NotAllowedError as Permission denied.

#### put_Handled

By default, both the `ScreenCaptureStarting` event handlers on the `CoreWebView2Frame` and the `CoreWebView2` will be invoked, with the `CoreWebView2Frame` event handlers invoked first.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

The host may set this flag to `TRUE` within the `CoreWebView2Frame` event handlers to prevent the remaining `CoreWebView2` event handlers from being invoked. If the flag is set to `FALSE` within the `CoreWebView2Frame` event handlers, downstream handlers can update the `Cancel` property.

If a deferral is taken on the event args, then you must synchronously set `Handled` to TRUE prior to taking your deferral to prevent the `CoreWebView2`s event handlers from being invoked.

