---
description: This is a continuation of the ICoreWebView2PermissionRequestedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs2
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2PermissionRequestedEventArgs2
- ICoreWebView2PermissionRequestedEventArgs2.get_Handled
- ICoreWebView2PermissionRequestedEventArgs2.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PermissionRequestedEventArgs2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2PermissionRequestedEventArgs2
  : public ICoreWebView2PermissionRequestedEventArgs
```

This is a continuation of the [ICoreWebView2PermissionRequestedEventArgs](icorewebview2permissionrequestedeventargs.md#icorewebview2permissionrequestedeventargs) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets the `Handled` property.
[put_Handled](#put_handled) | By default, both the `PermissionRequested` event handlers on the `CoreWebView2Frame` and the `CoreWebView2` will be invoked, with the `CoreWebView2Frame` event handlers invoked first.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### put_Handled

By default, both the `PermissionRequested` event handlers on the `CoreWebView2Frame` and the `CoreWebView2` will be invoked, with the `CoreWebView2Frame` event handlers invoked first.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

The host may set this flag to `TRUE` within the `CoreWebView2Frame` event handlers to prevent the remaining `CoreWebView2` event handlers from being invoked.

If a deferral is taken on the event args, then you must synchronously set `Handled` to TRUE prior to taking your deferral to prevent the `CoreWebView2`s event handlers from being invoked.

