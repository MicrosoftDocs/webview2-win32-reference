---
description: Window features for a WebView popup window.
title: WebView2 Win32 C++ ICoreWebView2WindowFeatures
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/20/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WindowFeatures
---

# interface ICoreWebView2WindowFeatures 

```
interface ICoreWebView2WindowFeatures
  : public IUnknown
```

Window features for a WebView popup window.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasPosition](#get_hasposition) | True if the Left and Top properties were specified.
[get_HasSize](#get_hassize) | True if the Width and Height properties were specified.
[get_Height](#get_height) | The height of the window. This will fail if HasSize is false.
[get_Left](#get_left) | The left position of the window. This will fail if HasPosition is false.
[get_ShouldDisplayMenuBar](#get_shoulddisplaymenubar) | Whether or not to display the menu bar.
[get_ShouldDisplayScrollBars](#get_shoulddisplayscrollbars) | Whether or not to display scroll bars.
[get_ShouldDisplayStatus](#get_shoulddisplaystatus) | Whether or not to display a status bar.
[get_ShouldDisplayToolbar](#get_shoulddisplaytoolbar) | Whether or not to display a toolbar.
[get_Top](#get_top) | The top position of the window. This will fail if HasPosition is false.
[get_Width](#get_width) | The width of the window. This will fail if HasSize is false.

These fields match the 'windowFeatures' passed to window.open as specified in [https://developer.mozilla.org/docs/Web/API/Window/open#Window_features](https://developer.mozilla.org/docs/Web/API/Window/open#Window_features) There is no requirement for you to respect these values. If your app doesn't have corresponding UI features, for example no toolbar, or if all webviews are opened in tabs and so cannot have distinct size or positions, then your app cannot respect these values. You may want to respect values but perhaps only some can apply to your app's UI. Accordingly, it is fine to respect all, some, or none of these properties as appropriate based on your app. For all numeric properties, if the value when passed to window.open is outside the range of an unsigned 32bit int, the value will be mod of the max of unsigned 32bit integer. If the value cannot be parsed as an integer it will be considered 0. If the value is a floating point value, it will be rounded down to an integer.

## Members

#### get_HasPosition 

True if the Left and Top properties were specified.

> public HRESULT [get_HasPosition](#get_hasposition)(BOOL * value)

False if at least one was not specified.

#### get_HasSize 

True if the Width and Height properties were specified.

> public HRESULT [get_HasSize](#get_hassize)(BOOL * value)

False if at least one was not specified.

#### get_Height 

The height of the window. This will fail if HasSize is false.

> public HRESULT [get_Height](#get_height)(UINT32 * value)

#### get_Left 

The left position of the window. This will fail if HasPosition is false.

> public HRESULT [get_Left](#get_left)(UINT32 * value)

#### get_ShouldDisplayMenuBar 

Whether or not to display the menu bar.

> public HRESULT [get_ShouldDisplayMenuBar](#get_shoulddisplaymenubar)(BOOL * value)

#### get_ShouldDisplayScrollBars 

Whether or not to display scroll bars.

> public HRESULT [get_ShouldDisplayScrollBars](#get_shoulddisplayscrollbars)(BOOL * value)

#### get_ShouldDisplayStatus 

Whether or not to display a status bar.

> public HRESULT [get_ShouldDisplayStatus](#get_shoulddisplaystatus)(BOOL * value)

#### get_ShouldDisplayToolbar 

Whether or not to display a toolbar.

> public HRESULT [get_ShouldDisplayToolbar](#get_shoulddisplaytoolbar)(BOOL * value)

#### get_Top 

The top position of the window. This will fail if HasPosition is false.

> public HRESULT [get_Top](#get_top)(UINT32 * value)

#### get_Width 

The width of the window. This will fail if HasSize is false.

> public HRESULT [get_Width](#get_width)(UINT32 * value)

