---
description: This interface is an extension of the ICoreWebView2Environment that manages user data folder.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment5
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment5
---

# interface ICoreWebView2ExperimentalEnvironment5

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment5
  : public IUnknown
```

This interface is an extension of the [ICoreWebView2Environment](icorewebview2environment.md).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserDataFolder](#get_userdatafolder) | Returns the user data folder that all CoreWebView2's created from this environment are using.

An object implementing the ICoreWebView2ExperimentalEnvironment5 interface will also implement [ICoreWebView2Environment](icorewebview2environment.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_UserDataFolder

Returns the user data folder that all CoreWebView2's created from this environment are using.

> public HRESULT [get_UserDataFolder](#get_userdatafolder)(LPWSTR * value)

This could be either the value passed in by the developer when creating the environment object or the calculated one for default handling. And will always be an absolute path.

```cpp
        auto experimentalEnvironment5 =
            m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment5>();
        CHECK_FEATURE_RETURN(experimentalEnvironment5);
        wil::unique_cotaskmem_string userDataFolder;
        experimentalEnvironment5->get_UserDataFolder(&userDataFolder);
        MessageBox(
            m_mainWindow, userDataFolder.get(), L"User Data Folder",
            MB_OK);
```

