---
description: The caller implements this interface to handle the result of `GetNonDefaultPermissionSettings`.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalGetNonDefaultPermissionSettingsCompletedHandler
ms.date: 01/17/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalGetNonDefaultPermissionSettingsCompletedHandler
---

# interface ICoreWebView2ExperimentalGetNonDefaultPermissionSettingsCompletedHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalGetNonDefaultPermissionSettingsCompletedHandler
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
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Provides the permission setting collection for the requested permission kind.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ExperimentalPermissionSettingCollectionView](icorewebview2experimentalpermissionsettingcollectionview.md) * collectionView)

