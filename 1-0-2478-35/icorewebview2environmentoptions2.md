---
description: Additional options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions2
ms.date: 05/20/2024
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

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

    std::wstring args;
    args.append(L"--enable-features=ThirdPartyStoragePartitioning,PartitionedCookies");
    auto options = Microsoft::WRL::Make<CoreWebView2EnvironmentOptions>();
    options->put_AdditionalBrowserArguments(args.c_str());
    CHECK_FAILURE(
        options->put_AllowSingleSignOnUsingOSPrimaryAccount(m_AADSSOEnabled ? TRUE : FALSE));
    CHECK_FAILURE(options->put_ExclusiveUserDataFolderAccess(
        m_ExclusiveUserDataFolderAccess ? TRUE : FALSE));
    if (!m_language.empty())
        CHECK_FAILURE(options->put_Language(m_language.c_str()));
    CHECK_FAILURE(options->put_IsCustomCrashReportingEnabled(
        m_CustomCrashReportingEnabled ? TRUE : FALSE));

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions4> options4;
    if (options.As(&options4) == S_OK)
    {
        const WCHAR* allowedOrigins[1] = {L"https://*.example.com"};

        auto customSchemeRegistration =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"custom-scheme");
        customSchemeRegistration->SetAllowedOrigins(1, allowedOrigins);
        auto customSchemeRegistration2 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"wv2rocks");
        customSchemeRegistration2->put_TreatAsSecure(TRUE);
        customSchemeRegistration2->SetAllowedOrigins(1, allowedOrigins);
        customSchemeRegistration2->put_HasAuthorityComponent(TRUE);
        auto customSchemeRegistration3 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(
                L"custom-scheme-not-in-allowed-origins");
        ICoreWebView2CustomSchemeRegistration* registrations[3] = {
            customSchemeRegistration.Get(), customSchemeRegistration2.Get(),
            customSchemeRegistration3.Get()};
        options4->SetCustomSchemeRegistrations(
            2, static_cast<ICoreWebView2CustomSchemeRegistration**>(registrations));
    }

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions5> options5;
    if (options.As(&options5) == S_OK)
    {
        CHECK_FAILURE(
            options5->put_EnableTrackingPrevention(m_TrackingPreventionEnabled ? TRUE : FALSE));
    }

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions6> options6;
    if (options.As(&options6) == S_OK)
    {
        CHECK_FAILURE(options6->put_AreBrowserExtensionsEnabled(TRUE));
    }

    Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalEnvironmentOptions2> exp_options2;
    if (options.As(&exp_options2) == S_OK)
    {
        COREWEBVIEW2_SCROLLBAR_STYLE style = COREWEBVIEW2_SCROLLBAR_STYLE_FLUENT_OVERLAY;
        CHECK_FAILURE(exp_options2->put_ScrollBarStyle(style));
    }

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

