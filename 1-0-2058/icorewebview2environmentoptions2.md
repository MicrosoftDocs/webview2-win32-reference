---
description: 
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions2
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions2
- ICoreWebView2EnvironmentOptions2.get_ExclusiveUserDataFolderAccess
- ICoreWebView2EnvironmentOptions2.put_ExclusiveUserDataFolderAccess
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions2

```
interface ICoreWebView2EnvironmentOptions2
  : public ICoreWebView2EnvironmentOptions
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ExclusiveUserDataFolderAccess](#get_exclusiveuserdatafolderaccess) | Gets the `ExclusiveUserDataFolderAccess` property.
[put_ExclusiveUserDataFolderAccess](#put_exclusiveuserdatafolderaccess) | Sets the `ExclusiveUserDataFolderAccess` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_ExclusiveUserDataFolderAccess

Gets the `ExclusiveUserDataFolderAccess` property.

> public HRESULT [get_ExclusiveUserDataFolderAccess](#get_exclusiveuserdatafolderaccess)(BOOL * value)

#### put_ExclusiveUserDataFolderAccess

Sets the `ExclusiveUserDataFolderAccess` property.

> public HRESULT [put_ExclusiveUserDataFolderAccess](#put_exclusiveuserdatafolderaccess)(BOOL value)

