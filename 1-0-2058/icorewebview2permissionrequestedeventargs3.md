---
description: 
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventArgs3
topic_type: 
- APIRef
api_name:
- ICoreWebView2PermissionRequestedEventArgs3
- ICoreWebView2PermissionRequestedEventArgs3.get_SavesInProfile
- ICoreWebView2PermissionRequestedEventArgs3.put_SavesInProfile
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PermissionRequestedEventArgs3

```
interface ICoreWebView2PermissionRequestedEventArgs3
  : public ICoreWebView2PermissionRequestedEventArgs2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SavesInProfile](#get_savesinprofile) | Gets the `SavesInProfile` property.
[put_SavesInProfile](#put_savesinprofile) | Sets the `SavesInProfile` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_SavesInProfile

Gets the `SavesInProfile` property.

> public HRESULT [get_SavesInProfile](#get_savesinprofile)(BOOL * value)

#### put_SavesInProfile

Sets the `SavesInProfile` property.

> public HRESULT [put_SavesInProfile](#put_savesinprofile)(BOOL value)

