---
description: 
title: WebView2 Win32 C++ ICoreWebView2LaunchingExternalUriSchemeEventArgs
ms.date: 09/08/2023
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

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_InitiatingOrigin](#get_initiatingorigin) | Gets the `InitiatingOrigin` property.
[get_IsUserInitiated](#get_isuserinitiated) | Gets the `IsUserInitiated` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[GetDeferral](#getdeferral) | 
[put_Cancel](#put_cancel) | Sets the `Cancel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1905

## Members

#### get_Cancel

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_InitiatingOrigin

Gets the `InitiatingOrigin` property.

> public HRESULT [get_InitiatingOrigin](#get_initiatingorigin)(LPWSTR * value)

#### get_IsUserInitiated

Gets the `IsUserInitiated` property.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

