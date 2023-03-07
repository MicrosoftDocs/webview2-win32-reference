---
description: The caller implements this interface to handle the result of `GetNonDefaultPermissionSettings`.
title: WebView2 Win32 C++ ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
ms.date: 03/07/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
---

# interface ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler

```
interface ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
  : public IUnknown
```

The caller implements this interface to handle the result of `GetNonDefaultPermissionSettings`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the permission setting collection for the requested permission kind.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### Invoke

Provides the permission setting collection for the requested permission kind.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, ICoreWebView2PermissionSettingCollectionView * collectionView)

