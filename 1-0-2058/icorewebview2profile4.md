---
description: 
title: WebView2 Win32 C++ ICoreWebView2Profile4
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile4
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile4
- ICoreWebView2Profile4.SetPermissionState
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile4

```
interface ICoreWebView2Profile4
  : public ICoreWebView2Profile3
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[SetPermissionState](#setpermissionstate) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### SetPermissionState

> public HRESULT [SetPermissionState](#setpermissionstate)(COREWEBVIEW2_PERMISSION_KIND PermissionKind, LPCWSTR origin, COREWEBVIEW2_PERMISSION_STATE State, [ICoreWebView2SetPermissionStateCompletedHandler](icorewebview2setpermissionstatecompletedhandler.md) * handler)

