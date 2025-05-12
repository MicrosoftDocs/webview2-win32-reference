---
description: Event args for `LaunchingExternalUriScheme` event.
title: WebView2 Win32 C++ ICoreWebView2LaunchingExternalUriSchemeEventArgs
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2LaunchingExternalUriSchemeEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2LaunchingExternalUriSchemeEventArgs
- ICoreWebView2LaunchingExternalUriSchemeEventArgs.get_Cancel
- ICoreWebView2LaunchingExternalUriSchemeEventArgs.get_InitiatingOrigin
- ICoreWebView2LaunchingExternalUriSchemeEventArgs.get_IsUserInitiated
- ICoreWebView2LaunchingExternalUriSchemeEventArgs.get_Uri
- ICoreWebView2LaunchingExternalUriSchemeEventArgs.GetDeferral
- ICoreWebView2LaunchingExternalUriSchemeEventArgs.put_Cancel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2LaunchingExternalUriSchemeEventArgs

```
interface ICoreWebView2LaunchingExternalUriSchemeEventArgs
  : public IUnknown
```

Event args for `LaunchingExternalUriScheme` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | The event handler may set this property to `TRUE` to cancel the external URI scheme launch.
[get_InitiatingOrigin](#get_initiatingorigin) | The origin initiating the external URI scheme launch.
[get_IsUserInitiated](#get_isuserinitiated) | `TRUE` when the external URI scheme request was initiated through a user gesture.
[get_Uri](#get_uri) | The URI with the external URI scheme to be launched.
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_Cancel](#put_cancel) | Sets the `Cancel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### get_Cancel

The event handler may set this property to `TRUE` to cancel the external URI scheme launch.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

If set to `TRUE`, the external URI scheme will not be launched, and the default dialog is not displayed. This property can be used to replace the normal handling of launching an external URI scheme. The initial value of the `Cancel` property is `FALSE`.

#### get_InitiatingOrigin

The origin initiating the external URI scheme launch.

> public HRESULT [get_InitiatingOrigin](#get_initiatingorigin)(LPWSTR * value)

The origin will be an empty string if the request is initiated by calling `CoreWebView2.Navigate` on the external URI scheme. If a script initiates the navigation, the `InitiatingOrigin` will be the top-level document's `Source`, for example, if `window.location` is set to `"calculator://"`, the `InitiatingOrigin` will be set to `calculator://`. If the request is initiated from a child frame, the `InitiatingOrigin` will be the source of that child frame. If the `InitiatingOrigin` is [opaque](https://html.spec.whatwg.org/multipage/origin.html#concept-origin-opaque), the `InitiatingOrigin` reported in the event args will be its precursor origin. The precursor origin is the origin that created the opaque origin. For example, if a frame on example.com opens a subframe with a different opaque origin, the subframe's precursor origin is example.com.

#### get_IsUserInitiated

`TRUE` when the external URI scheme request was initiated through a user gesture.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * value)

> [!NOTE]
> Being initiated through a user gesture does not mean that user intended to access the associated resource.

#### get_Uri

The URI with the external URI scheme to be launched.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** value)

Use this operation to complete the event at a later time.

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

