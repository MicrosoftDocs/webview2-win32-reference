---
description: Additional options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions2
---

# interface ICoreWebView2EnvironmentOptions2

```
interface ICoreWebView2EnvironmentOptions2
  : public IUnknown
```

Additional options used to create WebView2 Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ExclusiveUserDataFolderAccess](#get_exclusiveuserdatafolderaccess) | Whether other processes can create WebView2 from WebView2Environment created with the same user data folder and therefore sharing the same WebView browser process instance.
[put_ExclusiveUserDataFolderAccess](#put_exclusiveuserdatafolderaccess) | Sets the `ExclusiveUserDataFolderAccess` property.

A default implementation is provided in `WebView2EnvironmentOptions.h`.

```cpp

    auto options = Microsoft::WRL::Make<CoreWebView2EnvironmentOptions>();
    CHECK_FAILURE(
        options->put_AllowSingleSignOnUsingOSPrimaryAccount(
        m_AADSSOEnabled ? TRUE : FALSE));
    CHECK_FAILURE(options->put_ExclusiveUserDataFolderAccess(
        m_ExclusiveUserDataFolderAccess ? TRUE : FALSE));
    if (!m_language.empty())
        CHECK_FAILURE(options->put_Language(m_language.c_str()));

    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, m_userDataFolder.c_str(), options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_ExclusiveUserDataFolderAccess

Whether other processes can create WebView2 from WebView2Environment created with the same user data folder and therefore sharing the same WebView browser process instance.

> public HRESULT [get_ExclusiveUserDataFolderAccess](#get_exclusiveuserdatafolderaccess)(BOOL * value)

Default is FALSE.

#### put_ExclusiveUserDataFolderAccess

Sets the `ExclusiveUserDataFolderAccess` property.

> public HRESULT [put_ExclusiveUserDataFolderAccess](#put_exclusiveuserdatafolderaccess)(BOOL value)

The `ExclusiveUserDataFolderAccess` property specifies that the WebView environment obtains exclusive access to the user data folder. If the user data folder is already being used by another WebView environment with a different value for `ExclusiveUserDataFolderAccess` property, the creation of a WebView2Controller using the environment object will fail with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`. When set as TRUE, no other WebView can be created from other processes using WebView2Environment objects with the same UserDataFolder. This prevents other processes from creating WebViews which share the same browser process instance, since sharing is performed among WebViews that have the same UserDataFolder. When another process tries to create a WebView2Controller from an WebView2Environment object created with the same user data folder, it will fail with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`.

