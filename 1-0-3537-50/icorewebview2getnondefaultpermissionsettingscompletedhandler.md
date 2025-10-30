---
description: Receives the result of the `GetNonDefaultPermissionSettings` method.
title: WebView2 Win32 C++ ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
ms.date: 09/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
- ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2GetNonDefaultPermissionSettingsCompletedHandler
  : public IUnknown
```

Receives the result of the `GetNonDefaultPermissionSettings` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2PermissionSettingCollectionView](icorewebview2permissionsettingcollectionview.md#icorewebview2permissionsettingcollectionview) * result)

