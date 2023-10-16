---
description: This is the ICoreWebView2Experimental23 that provides the `FrameId` property.
title: WebView2 Win32 C++ ICoreWebView2Experimental23
ms.date: 10/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental23
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental23
- ICoreWebView2Experimental23.get_FrameId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental23

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental23
  : public IUnknown
```

This is the ICoreWebView2Experimental23 that provides the `FrameId` property.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FrameId](#get_frameid) | The unique identifier of the main frame.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### get_FrameId

The unique identifier of the main frame.

> public HRESULT [get_FrameId](#get_frameid)(UINT32 * id)

It's the same kind of ID as with the `FrameId` in `CoreWebView2Frame` and via `CoreWebView2FrameInfo`. Note that `FrameId` may not be valid if `CoreWebView` has not done any navigation. It's safe to get this value during or after the first `ContentLoading` event. Otherwise, it could return the invalid frame Id 0.

