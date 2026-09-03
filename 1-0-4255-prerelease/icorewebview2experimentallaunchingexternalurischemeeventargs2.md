---
description: This is a continuation of the ICoreWebView2LaunchingExternalUriSchemeEventArgs interface that adds the `Handled` property.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2
- ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2.get_Handled
- ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalLaunchingExternalUriSchemeEventArgs2
  : public IUnknown
```

This is a continuation of the [ICoreWebView2LaunchingExternalUriSchemeEventArgs](icorewebview2launchingexternalurischemeeventargs.md#icorewebview2launchingexternalurischemeeventargs) interface that adds the `Handled` property.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets the `Handled` property.
[put_Handled](#put_handled) | Indicates whether a `CoreWebView2Frame` event handler has handled this `LaunchingExternalUriScheme` event.

The `Handled` property is set from within an iframe-level `LaunchingExternalUriScheme` event handler to prevent the webview-level event handlers from being invoked for the same launch.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### put_Handled

Indicates whether a `CoreWebView2Frame` event handler has handled this `LaunchingExternalUriScheme` event.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

Defaults to `FALSE`.

By default, the `LaunchingExternalUriScheme` event handlers on the `CoreWebView2Frame` and the `CoreWebView2` are all invoked, with the `CoreWebView2Frame` event handlers invoked first, innermost frame first for nested iframes. The host may set this flag to `TRUE` within a `CoreWebView2Frame` event handler to prevent the remaining ancestor `CoreWebView2Frame` and `CoreWebView2` event handlers from being invoked.

Setting `Handled` has no effect when the event is raised on `CoreWebView2`; it only suppresses the remaining handlers when set from a `CoreWebView2Frame` handler.

If a deferral is taken on the event args, then you must synchronously set `Handled` to `TRUE` prior to taking your deferral to prevent the remaining ancestor frame and `CoreWebView2` event handlers from being invoked.

