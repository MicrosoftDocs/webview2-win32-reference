---
description: This interface is an extension of the ICoreWebView2Environment.
title: WebView2 Win32 C++ ICoreWebView2Environment7
ms.date: 05/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment7
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment7
- ICoreWebView2Environment7.get_UserDataFolder
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment7

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Environment7
  : public ICoreWebView2Environment6
```

This interface is an extension of the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserDataFolder](#get_userdatafolder) | Returns the user data folder that all CoreWebView2's created from this environment are using.

An object implementing the ICoreWebView2Environment7 interface will also implement [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1054.31
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### get_UserDataFolder

Returns the user data folder that all CoreWebView2's created from this environment are using.

> public HRESULT [get_UserDataFolder](#get_userdatafolder)(LPWSTR * value)

This could be either the value passed in by the developer when creating the environment object or the calculated one for default handling. It will always be an absolute path.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

```cpp
        auto environment7 = m_webViewEnvironment.try_query<ICoreWebView2Environment7>();
        CHECK_FEATURE_RETURN(environment7);
        wil::unique_cotaskmem_string userDataFolder;
        environment7->get_UserDataFolder(&userDataFolder);
        MessageBox(m_mainWindow, userDataFolder.get(), L"User Data Folder", MB_OK);
```

