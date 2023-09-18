---
description: 
title: WebView2 Win32 C++ ICoreWebView2ControllerOptions
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerOptions
- ICoreWebView2ControllerOptions.get_IsInPrivateModeEnabled
- ICoreWebView2ControllerOptions.get_ProfileName
- ICoreWebView2ControllerOptions.put_IsInPrivateModeEnabled
- ICoreWebView2ControllerOptions.put_ProfileName
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerOptions

```
interface ICoreWebView2ControllerOptions
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled) | Gets the `IsInPrivateModeEnabled` property.
[get_ProfileName](#get_profilename) | Gets the `ProfileName` property.
[put_IsInPrivateModeEnabled](#put_isinprivatemodeenabled) | Sets the `IsInPrivateModeEnabled` property.
[put_ProfileName](#put_profilename) | Sets the `ProfileName` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1210.39
WebView2 Win32 Prerelease |    1.0.1222

## Members

#### get_IsInPrivateModeEnabled

Gets the `IsInPrivateModeEnabled` property.

> public HRESULT [get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled)(BOOL * value)

#### get_ProfileName

Gets the `ProfileName` property.

> public HRESULT [get_ProfileName](#get_profilename)(LPWSTR * value)

#### put_IsInPrivateModeEnabled

Sets the `IsInPrivateModeEnabled` property.

> public HRESULT [put_IsInPrivateModeEnabled](#put_isinprivatemodeenabled)(BOOL value)

#### put_ProfileName

Sets the `ProfileName` property.

> public HRESULT [put_ProfileName](#put_profilename)(LPCWSTR value)

