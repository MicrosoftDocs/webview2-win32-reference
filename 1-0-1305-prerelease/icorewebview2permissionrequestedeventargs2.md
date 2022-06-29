---
description: This is a continuation of the ICoreWebView2PermissionRequestedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventArgs2
---

# interface ICoreWebView2PermissionRequestedEventArgs2

```
interface ICoreWebView2PermissionRequestedEventArgs2
  : public ICoreWebView2PermissionRequestedEventArgs
```

This is a continuation of the ICoreWebView2PermissionRequestedEventArgs interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | By default, both the `PermissionRequested` event handlers on the CoreWebView2Frame and the `CoreWebView2` will be invoked, with the CoreWebView2Frame event handlers invoked first.
[put_Handled](#put_handled) | Sets the `Handled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### get_Handled

By default, both the `PermissionRequested` event handlers on the CoreWebView2Frame and the `CoreWebView2` will be invoked, with the CoreWebView2Frame event handlers invoked first.

> public HRESULT [get_Handled](#get_handled)(BOOL * handled)

The host may set this flag to `TRUE` within the CoreWebView2Frame event handlers to prevent the remaining `CoreWebView2` event handlers from being invoked.

If a deferral is taken on the event args, then you must synchronously set `Handled` to TRUE prior to taking your deferral to prevent the `CoreWebView2`s event handlers from being invoked.

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL handled)

