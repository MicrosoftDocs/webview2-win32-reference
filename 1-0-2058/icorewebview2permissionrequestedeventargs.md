---
description: 
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2PermissionRequestedEventArgs
- ICoreWebView2PermissionRequestedEventArgs.get_IsUserInitiated
- ICoreWebView2PermissionRequestedEventArgs.get_PermissionKind
- ICoreWebView2PermissionRequestedEventArgs.get_State
- ICoreWebView2PermissionRequestedEventArgs.get_Uri
- ICoreWebView2PermissionRequestedEventArgs.GetDeferral
- ICoreWebView2PermissionRequestedEventArgs.put_State
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PermissionRequestedEventArgs

```
interface ICoreWebView2PermissionRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsUserInitiated](#get_isuserinitiated) | Gets the `IsUserInitiated` property.
[get_PermissionKind](#get_permissionkind) | Gets the `PermissionKind` property.
[get_State](#get_state) | Gets the `State` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[GetDeferral](#getdeferral) | 
[put_State](#put_state) | Sets the `State` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsUserInitiated

Gets the `IsUserInitiated` property.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * value)

#### get_PermissionKind

Gets the `PermissionKind` property.

> public HRESULT [get_PermissionKind](#get_permissionkind)(COREWEBVIEW2_PERMISSION_KIND * value)

#### get_State

Gets the `State` property.

> public HRESULT [get_State](#get_state)(COREWEBVIEW2_PERMISSION_STATE * value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_State

Sets the `State` property.

> public HRESULT [put_State](#put_state)(COREWEBVIEW2_PERMISSION_STATE value)

