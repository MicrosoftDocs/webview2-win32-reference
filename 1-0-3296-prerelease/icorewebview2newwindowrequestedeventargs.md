---
description: Event args for the `NewWindowRequested` event.
title: WebView2 Win32 C++ ICoreWebView2NewWindowRequestedEventArgs
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewWindowRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2NewWindowRequestedEventArgs
- ICoreWebView2NewWindowRequestedEventArgs.get_Handled
- ICoreWebView2NewWindowRequestedEventArgs.get_IsUserInitiated
- ICoreWebView2NewWindowRequestedEventArgs.get_NewWindow
- ICoreWebView2NewWindowRequestedEventArgs.get_Uri
- ICoreWebView2NewWindowRequestedEventArgs.get_WindowFeatures
- ICoreWebView2NewWindowRequestedEventArgs.GetDeferral
- ICoreWebView2NewWindowRequestedEventArgs.put_Handled
- ICoreWebView2NewWindowRequestedEventArgs.put_NewWindow
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
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
[get_IsUserInitiated](#get_isuserinitiated) | `TRUE` when the new window request was initiated through a user gesture.
[get_NewWindow](#get_newwindow) | Gets the new window.
[get_Uri](#get_uri) | The target uri of the new window requested.
[get_WindowFeatures](#get_windowfeatures) | Window features specified by the `window.open`.
[GetDeferral](#getdeferral) | Obtain an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object and put the event into a deferred state.
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

> public HRESULT [get_NewWindow](#get_newwindow)([ICoreWebView2](icorewebview2.md#icorewebview2) ** newWindow)

#### get_Uri

The target uri of the new window requested.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_WindowFeatures

Window features specified by the `window.open`.

> public HRESULT [get_WindowFeatures](#get_windowfeatures)([ICoreWebView2WindowFeatures](icorewebview2windowfeatures.md#icorewebview2windowfeatures) ** value)

The features should be considered for positioning and sizing of new webview windows.

#### GetDeferral

Obtain an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object and put the event into a deferred state.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** deferral)

Use the [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object to complete the window open request at a later time. While this event is deferred the opener window returns a `WindowProxy` to an un-navigated window, which navigates when the deferral is complete.

#### put_Handled

Sets whether the `NewWindowRequested` event is handled by host.

> public HRESULT [put_Handled](#put_handled)(BOOL handled)

If this is `FALSE` and no `NewWindow` is set, the WebView opens a popup window and it returns as opened `WindowProxy`. If set to `TRUE` and no `NewWindow` is set for `window.open`, the opened `WindowProxy` is for an testing window object and no window loads. The default value is `FALSE`.

#### put_NewWindow

Sets a CoreWebView2 as a result of the NewWindowRequested event.

> public HRESULT [put_NewWindow](#put_newwindow)([ICoreWebView2](icorewebview2.md#icorewebview2) * newWindow)

Provides a WebView as the target for a `window.open()` from inside the requesting WebView. If this is set, the top-level window of this WebView is returned as the opened [WindowProxy](https://developer.mozilla.org/docs/glossary/windowproxy) to the opener script. If this is not set, then `Handled` is checked to determine behavior for NewWindowRequested event. CoreWebView2 provided in the `NewWindow` property must be on the same Environment as the opener WebView and should not have been navigated previously. Don't use methods that cause navigation or interact with the DOM on this CoreWebView2 until the target content has loaded. Setting event handlers, changing Settings properties, or other methods are fine to call. Changes to settings should be made before `put_NewWindow` is called to ensure that those settings take effect for the newly setup WebView. Once the NewWindow is set the underlying web contents of this CoreWebView2 will be replaced and navigated as appropriate for the new window. After setting new window it cannot be changed and error will be return otherwise.

The methods which should affect the new web contents like AddScriptToExecuteOnDocumentCreated has to be called and completed before setting NewWindow. Other methods which should affect the new web contents like add_WebResourceRequested have to be called after setting NewWindow. It is best not to use RemoveScriptToExecuteOnDocumentCreated before setting NewWindow, otherwise it may not work for later added scripts.

The new WebView must have the same profile as the opener WebView.

