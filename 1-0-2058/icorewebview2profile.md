---
description: 
title: WebView2 Win32 C++ ICoreWebView2Profile
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile
- ICoreWebView2Profile.get_DefaultDownloadFolderPath
- ICoreWebView2Profile.get_IsInPrivateModeEnabled
- ICoreWebView2Profile.get_PreferredColorScheme
- ICoreWebView2Profile.get_ProfileName
- ICoreWebView2Profile.get_ProfilePath
- ICoreWebView2Profile.put_DefaultDownloadFolderPath
- ICoreWebView2Profile.put_PreferredColorScheme
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile

```
interface ICoreWebView2Profile
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultDownloadFolderPath](#get_defaultdownloadfolderpath) | Gets the `DefaultDownloadFolderPath` property.
[get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled) | Gets the `IsInPrivateModeEnabled` property.
[get_PreferredColorScheme](#get_preferredcolorscheme) | Gets the `PreferredColorScheme` property.
[get_ProfileName](#get_profilename) | Gets the `ProfileName` property.
[get_ProfilePath](#get_profilepath) | Gets the `ProfilePath` property.
[put_DefaultDownloadFolderPath](#put_defaultdownloadfolderpath) | Sets the `DefaultDownloadFolderPath` property.
[put_PreferredColorScheme](#put_preferredcolorscheme) | Sets the `PreferredColorScheme` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1210.39
WebView2 Win32 Prerelease |    1.0.1222

## Members

#### get_DefaultDownloadFolderPath

Gets the `DefaultDownloadFolderPath` property.

> public HRESULT [get_DefaultDownloadFolderPath](#get_defaultdownloadfolderpath)(LPWSTR * value)

#### get_IsInPrivateModeEnabled

Gets the `IsInPrivateModeEnabled` property.

> public HRESULT [get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled)(BOOL * value)

#### get_PreferredColorScheme

Gets the `PreferredColorScheme` property.

> public HRESULT [get_PreferredColorScheme](#get_preferredcolorscheme)(COREWEBVIEW2_PREFERRED_COLOR_SCHEME * value)

#### get_ProfileName

Gets the `ProfileName` property.

> public HRESULT [get_ProfileName](#get_profilename)(LPWSTR * value)

#### get_ProfilePath

Gets the `ProfilePath` property.

> public HRESULT [get_ProfilePath](#get_profilepath)(LPWSTR * value)

#### put_DefaultDownloadFolderPath

Sets the `DefaultDownloadFolderPath` property.

> public HRESULT [put_DefaultDownloadFolderPath](#put_defaultdownloadfolderpath)(LPCWSTR value)

#### put_PreferredColorScheme

Sets the `PreferredColorScheme` property.

> public HRESULT [put_PreferredColorScheme](#put_preferredcolorscheme)(COREWEBVIEW2_PREFERRED_COLOR_SCHEME value)

