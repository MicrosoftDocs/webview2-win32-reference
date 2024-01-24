---
description: Event args for the `NewWindowRequested` event.
title: WebView2 Win32 C++ ICoreWebView2NewWindowRequestedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 01/29/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewWindowRequestedEventArgs
---

# interface ICoreWebView2NewWindowRequestedEventArgs 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2NewWindowRequestedEventArgs
  : public IUnknown
```

Event args for the `NewWindowRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets whether the `NewWindowRequested` event is handled by host.
[get_IsUserInitiated](#get_isuserinitiated) | `TRUE` when the new window request was initiated through a user gesture such as selecting an anchor tag with target.
[get_NewWindow](#get_newwindow) | Gets the new window.
[get_Uri](#get_uri) | The target uri of the new window requested.
[get_WindowFeatures](#get_windowfeatures) | Window features specified by the `window.open`.
[GetDeferral](#getdeferral) | Obtain an `[ICoreWebView2Deferral](icorewebview2deferral.md)` object and put the event into a deferred state.
[put_Handled](#put_handled) | Sets whether the `NewWindowRequested` event is handled by host.
[put_NewWindow](#put_newwindow) | Sets a WebView as a result of the `NewWindowRequested`.

The event is run when content inside webview requested to a open a new window (through `window.open()` and so on).

## Members

#### get_Handled 

Gets whether the `NewWindowRequested` event is handled by host.

> public HRESULT [get_Handled](#get_handled)(BOOL * handled)

#### get_IsUserInitiated 

`TRUE` when the new window request was initiated through a user gesture such as selecting an anchor tag with target.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * isUserInitiated)

The Microsoft Edge popup blocker is disabled for WebView so the app is able to use this flag to block non-user initiated popups.

#### get_NewWindow 

Gets the new window.

> public HRESULT [get_NewWindow](#get_newwindow)([ICoreWebView2](icorewebview2.md) ** newWindow)

#### get_Uri 

The target uri of the new window requested.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

#### get_WindowFeatures 

Window features specified by the `window.open`.

> public HRESULT [get_WindowFeatures](#get_windowfeatures)([ICoreWebView2WindowFeatures](icorewebview2windowfeatures.md) ** value)

The features should be considered for positioning and sizing of new webview windows.

#### GetDeferral 

Obtain an `[ICoreWebView2Deferral](icorewebview2deferral.md)` object and put the event into a deferred state.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md) ** deferral)

Use the `[ICoreWebView2Deferral](icorewebview2deferral.md)` object to complete the window open request at a later time. While this event is deferred the opener window returns a `WindowProxy` to an un-navigated window, which navigates when the deferral is complete.

#### put_Handled 

Sets whether the `NewWindowRequested` event is handled by host.

> public HRESULT [put_Handled](#put_handled)(BOOL handled)

If this is `FALSE` and no `NewWindow` is set, the WebView opens a popup window and it returns as opened `WindowProxy`. If set to `TRUE` and no `NewWindow` is set for `window.open`, the opened `WindowProxy` is for an testing window object and no window loads. The default value is `FALSE`.

#### put_NewWindow 

Sets a WebView as a result of the `NewWindowRequested`.

> public HRESULT [put_NewWindow](#put_newwindow)([ICoreWebView2](icorewebview2.md) * newWindow)

The target WebView should not be navigated. If the `NewWindow` is set, the top-level window returns as the opened `WindowProxy`.

