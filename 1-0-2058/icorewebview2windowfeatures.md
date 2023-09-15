---
description: 
title: WebView2 Win32 C++ ICoreWebView2WindowFeatures
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WindowFeatures
topic_type: 
- APIRef
api_name:
- ICoreWebView2WindowFeatures
- ICoreWebView2WindowFeatures.get_HasPosition
- ICoreWebView2WindowFeatures.get_HasSize
- ICoreWebView2WindowFeatures.get_Height
- ICoreWebView2WindowFeatures.get_Left
- ICoreWebView2WindowFeatures.get_ShouldDisplayMenuBar
- ICoreWebView2WindowFeatures.get_ShouldDisplayScrollBars
- ICoreWebView2WindowFeatures.get_ShouldDisplayStatus
- ICoreWebView2WindowFeatures.get_ShouldDisplayToolbar
- ICoreWebView2WindowFeatures.get_Top
- ICoreWebView2WindowFeatures.get_Width
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WindowFeatures

```
interface ICoreWebView2WindowFeatures
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasPosition](#get_hasposition) | Gets the `HasPosition` property.
[get_HasSize](#get_hassize) | Gets the `HasSize` property.
[get_Height](#get_height) | Gets the `Height` property.
[get_Left](#get_left) | Gets the `Left` property.
[get_ShouldDisplayMenuBar](#get_shoulddisplaymenubar) | Gets the `ShouldDisplayMenuBar` property.
[get_ShouldDisplayScrollBars](#get_shoulddisplayscrollbars) | Gets the `ShouldDisplayScrollBars` property.
[get_ShouldDisplayStatus](#get_shoulddisplaystatus) | Gets the `ShouldDisplayStatus` property.
[get_ShouldDisplayToolbar](#get_shoulddisplaytoolbar) | Gets the `ShouldDisplayToolbar` property.
[get_Top](#get_top) | Gets the `Top` property.
[get_Width](#get_width) | Gets the `Width` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.622.11
WebView2 Win32 Prerelease |    0.9.628

## Members

#### get_HasPosition

Gets the `HasPosition` property.

> public HRESULT [get_HasPosition](#get_hasposition)(BOOL * value)

#### get_HasSize

Gets the `HasSize` property.

> public HRESULT [get_HasSize](#get_hassize)(BOOL * value)

#### get_Height

Gets the `Height` property.

> public HRESULT [get_Height](#get_height)(UINT32 * value)

#### get_Left

Gets the `Left` property.

> public HRESULT [get_Left](#get_left)(UINT32 * value)

#### get_ShouldDisplayMenuBar

Gets the `ShouldDisplayMenuBar` property.

> public HRESULT [get_ShouldDisplayMenuBar](#get_shoulddisplaymenubar)(BOOL * value)

#### get_ShouldDisplayScrollBars

Gets the `ShouldDisplayScrollBars` property.

> public HRESULT [get_ShouldDisplayScrollBars](#get_shoulddisplayscrollbars)(BOOL * value)

#### get_ShouldDisplayStatus

Gets the `ShouldDisplayStatus` property.

> public HRESULT [get_ShouldDisplayStatus](#get_shoulddisplaystatus)(BOOL * value)

#### get_ShouldDisplayToolbar

Gets the `ShouldDisplayToolbar` property.

> public HRESULT [get_ShouldDisplayToolbar](#get_shoulddisplaytoolbar)(BOOL * value)

#### get_Top

Gets the `Top` property.

> public HRESULT [get_Top](#get_top)(UINT32 * value)

#### get_Width

Gets the `Width` property.

> public HRESULT [get_Width](#get_width)(UINT32 * value)

