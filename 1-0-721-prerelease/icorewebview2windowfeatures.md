---
description: The window features for a WebView popup window.
title: WebView2 Win32 C++ ICoreWebView2WindowFeatures
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/29/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WindowFeatures
---

# interface ICoreWebView2WindowFeatures 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2WindowFeatures
  : public IUnknown
```

The window features for a WebView popup window.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasPosition](#get_hasposition) | Specifies left and top values.
[get_HasSize](#get_hassize) | Specifiesheight and width values.
[get_Height](#get_height) | Specifies the height of the window.
[get_Left](#get_left) | Specifies the left position of the window.
[get_ShouldDisplayMenuBar](#get_shoulddisplaymenubar) | Indicates that the menu bar is displayed.
[get_ShouldDisplayScrollBars](#get_shoulddisplayscrollbars) | Indicates that the scroll bars are displayed.
[get_ShouldDisplayStatus](#get_shoulddisplaystatus) | Indicates that the status bar is displayed.
[get_ShouldDisplayToolbar](#get_shoulddisplaytoolbar) | Indicates that the browser toolbar is displayed.
[get_Top](#get_top) | Specifies the top position of the window.
[get_Width](#get_width) | Specifies the width of the window.

The fields match the `windowFeatures` passed to `window.open` as specified in [Window features][MdnDocsWebApiWindowOpenWindowFeatures] on MDN. There is no requirement for you to respect the values. If your app does not have corresponding UI features (for example, no toolbar) or if all instance of WebView are opened in tabs and do not have distinct size or positions, then your app does not respect the values. You may want to respect values, but perhaps only some apply to the UI of you app. Accordingly, you may respect all, some, or none of the properties as appropriate for your app. For all numeric properties, if the value that is passed to `window.open` is outside the range of an unsigned 32bit int, the resulting value is the absolute value of the maximum for unsigned 32bit integer. If you are not able to parse the value an integer, it is considered `0`. If the value is a floating point value, it is rounded down to an integer.

[MdnDocsWebApiWindowOpenWindowFeatures]: https://developer.mozilla.org/docs/Web/API/Window/open#Window_features "Window features - Window.open() | MDN"

## Members

#### get_HasPosition 

Specifies left and top values.

> public HRESULT [get_HasPosition](#get_hasposition)(BOOL * value)

#### get_HasSize 

Specifiesheight and width values.

> public HRESULT [get_HasSize](#get_hassize)(BOOL * value)

#### get_Height 

Specifies the height of the window.

> public HRESULT [get_Height](#get_height)(UINT32 * value)

Minimum value is `100`. If `HasSize` is set to `FALSE`, this field is ignored.

#### get_Left 

Specifies the left position of the window.

> public HRESULT [get_Left](#get_left)(UINT32 * value)

If `HasPosition` is set to `FALSE`, this field is ignored.

#### get_ShouldDisplayMenuBar 

Indicates that the menu bar is displayed.

> public HRESULT [get_ShouldDisplayMenuBar](#get_shoulddisplaymenubar)(BOOL * value)

#### get_ShouldDisplayScrollBars 

Indicates that the scroll bars are displayed.

> public HRESULT [get_ShouldDisplayScrollBars](#get_shoulddisplayscrollbars)(BOOL * value)

#### get_ShouldDisplayStatus 

Indicates that the status bar is displayed.

> public HRESULT [get_ShouldDisplayStatus](#get_shoulddisplaystatus)(BOOL * value)

#### get_ShouldDisplayToolbar 

Indicates that the browser toolbar is displayed.

> public HRESULT [get_ShouldDisplayToolbar](#get_shoulddisplaytoolbar)(BOOL * value)

#### get_Top 

Specifies the top position of the window.

> public HRESULT [get_Top](#get_top)(UINT32 * value)

If `HasPosition` is set to `FALSE`, this field is ignored.

#### get_Width 

Specifies the width of the window.

> public HRESULT [get_Width](#get_width)(UINT32 * value)

Minimum value is `100`. If `HasSize` is set to `FALSE`, this field is ignored.

