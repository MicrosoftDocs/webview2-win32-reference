---
description: 
title: WebView2 Win32 C++ ICoreWebView2PermissionSetting
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionSetting
topic_type: 
- APIRef
api_name:
- ICoreWebView2PermissionSetting
- ICoreWebView2PermissionSetting.get_PermissionKind
- ICoreWebView2PermissionSetting.get_PermissionOrigin
- ICoreWebView2PermissionSetting.get_PermissionState
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PermissionSetting

```
interface ICoreWebView2PermissionSetting
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_PermissionKind](#get_permissionkind) | Gets the `PermissionKind` property.
[get_PermissionOrigin](#get_permissionorigin) | Gets the `PermissionOrigin` property.
[get_PermissionState](#get_permissionstate) | Gets the `PermissionState` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_PermissionKind

Gets the `PermissionKind` property.

> public HRESULT [get_PermissionKind](#get_permissionkind)(COREWEBVIEW2_PERMISSION_KIND * value)

#### get_PermissionOrigin

Gets the `PermissionOrigin` property.

> public HRESULT [get_PermissionOrigin](#get_permissionorigin)(LPWSTR * value)

#### get_PermissionState

Gets the `PermissionState` property.

> public HRESULT [get_PermissionState](#get_permissionstate)(COREWEBVIEW2_PERMISSION_STATE * value)

