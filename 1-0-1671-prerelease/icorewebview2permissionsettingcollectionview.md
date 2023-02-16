---
description: Read-only collection of `PermissionSetting`s (origin, kind, and state).
title: WebView2 Win32 C++ ICoreWebView2PermissionSettingCollectionView
ms.date: 02/14/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionSettingCollectionView
---

# interface ICoreWebView2PermissionSettingCollectionView

```
interface ICoreWebView2PermissionSettingCollectionView
  : public IUnknown
```

Read-only collection of `PermissionSetting`s (origin, kind, and state).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | The number of ICoreWebView2PermissionSettings in the collection.
[GetValueAtIndex](#getvalueatindex) | Gets the ICoreWebView2PermissionSetting at the specified index.

Used to list the nondefault permission settings on the profile that are persisted across sessions.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_Count

The number of ICoreWebView2PermissionSettings in the collection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the ICoreWebView2PermissionSetting at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, ICoreWebView2PermissionSetting ** permissionSetting)

