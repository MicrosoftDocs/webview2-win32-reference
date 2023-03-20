---
description: Provides a set of properties for a permission setting.
title: WebView2 Win32 C++ ICoreWebView2PermissionSetting
ms.date: 03/13/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionSetting
---

# interface ICoreWebView2PermissionSetting

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2PermissionSetting
  : public IUnknown
```

Provides a set of properties for a permission setting.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_PermissionKind](#get_permissionkind) | The kind of the permission setting.
[get_PermissionOrigin](#get_permissionorigin) | The origin of the permission setting.
[get_PermissionState](#get_permissionstate) | The state of the permission setting.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_PermissionKind

The kind of the permission setting.

> public HRESULT [get_PermissionKind](#get_permissionkind)(COREWEBVIEW2_PERMISSION_KIND * value)

See `COREWEBVIEW2_PERMISSION_KIND` for more details.

#### get_PermissionOrigin

The origin of the permission setting.

> public HRESULT [get_PermissionOrigin](#get_permissionorigin)(LPWSTR * value)

#### get_PermissionState

The state of the permission setting.

> public HRESULT [get_PermissionState](#get_permissionstate)(COREWEBVIEW2_PERMISSION_STATE * value)

