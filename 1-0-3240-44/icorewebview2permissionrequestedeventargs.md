---
description: Event args for the `PermissionRequested` event.
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs
ms.date: 04/29/2025
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2PermissionRequestedEventArgs
  : public IUnknown
```

Event args for the `PermissionRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsUserInitiated](#get_isuserinitiated) | `TRUE` when the permission request was initiated through a user gesture.
[get_PermissionKind](#get_permissionkind) | The type of the permission that is requested.
[get_State](#get_state) | The status of a permission request, (for example is the request is granted).
[get_Uri](#get_uri) | The origin of the web content that requests the permission.
[GetDeferral](#getdeferral) | Gets an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_State](#put_state) | Sets the `State` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsUserInitiated

`TRUE` when the permission request was initiated through a user gesture.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * isUserInitiated)

> [!NOTE]
> Being initiated through a user gesture does not mean that user intended to access the associated resource.

#### get_PermissionKind

The type of the permission that is requested.

> public HRESULT [get_PermissionKind](#get_permissionkind)(COREWEBVIEW2_PERMISSION_KIND * permissionKind)

#### get_State

The status of a permission request, (for example is the request is granted).

> public HRESULT [get_State](#get_state)(COREWEBVIEW2_PERMISSION_STATE * state)

The default value is `COREWEBVIEW2_PERMISSION_STATE_DEFAULT`.

#### get_Uri

The origin of the web content that requests the permission.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetDeferral

Gets an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** deferral)

Use the deferral object to make the permission decision at a later time. The deferral only applies to the current request, and does not prevent the `PermissionRequested` event from getting raised for new requests. However, for some permission kinds the WebView will avoid creating a new request if there is a pending request of the same kind.

#### put_State

Sets the `State` property.

> public HRESULT [put_State](#put_state)(COREWEBVIEW2_PERMISSION_STATE state)

