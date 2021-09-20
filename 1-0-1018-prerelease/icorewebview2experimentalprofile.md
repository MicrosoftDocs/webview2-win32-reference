---
description: Profile for ICoreWebView2Experimental8 interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/20/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile
---

# interface ICoreWebView2ExperimentalProfile

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile
  : public IUnknown
```

Profile for [ICoreWebView2Experimental8](icorewebview2experimental8.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled) | InPrivate mode is enabled or not.
[get_ProfileName](#get_profilename) | Name of the profile.
[get_ProfilePath](#get_profilepath) | Full path of the profile directory.

```cpp
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### get_IsInPrivateModeEnabled

InPrivate mode is enabled or not.

> public HRESULT [get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled)(BOOL * value)

#### get_ProfileName

Name of the profile.

> public HRESULT [get_ProfileName](#get_profilename)(LPWSTR * value)

#### get_ProfilePath

Full path of the profile directory.

> public HRESULT [get_ProfilePath](#get_profilepath)(LPWSTR * value)

