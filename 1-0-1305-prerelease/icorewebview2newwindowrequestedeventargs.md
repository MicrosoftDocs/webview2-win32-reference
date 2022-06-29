---
description: Event args for the `NewWindowRequested` event.
title: WebView2 Win32 C++ ICoreWebView2NewWindowRequestedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewWindowRequestedEventArgs
---

# interface ICoreWebView2NewWindowRequestedEventArgs

```
interface ICoreWebView2NewWindowRequestedEventArgs
  : public IUnknown
```

Event args for the `NewWindowRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets whether the `NewWindowRequested` event is handled by host.
[get_IsUserInitiated](#get_isuserinitiated) | `TRUE` when the new window request was initiated through a user gesture.
[get_NewWindow](#get_newwindow) | Gets the new window.
[get_Uri](#get_uri) | The target uri of the new window requested.
[get_WindowFeatures](#get_windowfeatures) | Window features specified by the `window.open`.
[GetDeferral](#getdeferral) | Obtain an ICoreWebView2Deferral object and put the event into a deferred state.
[put_Handled](#put_handled) | Sets whether the `NewWindowRequested` event is handled by host.
[put_NewWindow](#put_newwindow) | Sets a CoreWebView2 as a result of the NewWindowRequested event.

The event is run when content inside webview requested to a open a new window (through `window.open()` and so on).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Handled

Gets whether the `NewWindowRequested` event is handled by host.

> public HRESULT [get_Handled](#get_handled)(BOOL * handled)

#### get_IsUserInitiated

`TRUE` when the new window request was initiated through a user gesture.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * isUserInitiated)

Examples of user initiated requests are:

* Selecting an anchor tag with target

* Programmatic window open from a script that directly run as a result of user interaction such as via onclick handlers.

Non-user initiated requests are programmatic window opens from a script that are not directly triggered by user interaction, such as those that run while loading a new page or via timers. The Microsoft Edge popup blocker is disabled for WebView so the app is able to use this flag to block non-user initiated popups.

#### get_NewWindow

Gets the new window.

> public HRESULT [get_NewWindow](#get_newwindow)(ICoreWebView2 ** newWindow)

#### get_Uri

The target uri of the new window requested.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_WindowFeatures

Window features specified by the `window.open`.

> public HRESULT [get_WindowFeatures](#get_windowfeatures)(ICoreWebView2WindowFeatures ** value)

The features should be considered for positioning and sizing of new webview windows.

#### GetDeferral

Obtain an ICoreWebView2Deferral object and put the event into a deferred state.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use the ICoreWebView2Deferral object to complete the window open request at a later time. While this event is deferred the opener window returns a `WindowProxy` to an un-navigated window, which navigates when the deferral is complete.

#### put_Handled

Sets whether the `NewWindowRequested` event is handled by host.

> public HRESULT [put_Handled](#put_handled)(BOOL handled)

If this is `FALSE` and no `NewWindow` is set, the WebView opens a popup window and it returns as opened `WindowProxy`. If set to `TRUE` and no `NewWindow` is set for `window.open`, the opened `WindowProxy` is for an testing window object and no window loads. The default value is `FALSE`.

#### put_NewWindow

Sets a CoreWebView2 as a result of the NewWindowRequested event.

> public HRESULT [put_NewWindow](#put_newwindow)(ICoreWebView2 * newWindow)

If the `NewWindow` is set, the top-level window returns as the opened `WindowProxy`. The NewWindow property should be set to a CoreWebView2 that has not been navigated previously. Don't use methods that cause navigation or interact with the DOM on this CoreWebView2. Setting event handlers, changing Settings properties, or other methods are fine to call. Changes to settings should be made before `put_NewWindow` is called to ensure that those settings take effect for the newly setup WebView. Once the NewWindow is set the underlying web contents of this CoreWebView2 will be replaced and navigated as appropriate for the new window. After setting new window it cannot be changed and error will be return otherwise.

The methods which should affect the new web contents like AddScriptToExecuteOnDocumentCreated and add_WebResourceRequested have to be called after setting NewWindow.

The new WebView must have the same profile as the opener WebView.

