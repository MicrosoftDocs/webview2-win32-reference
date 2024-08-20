---
description: Additional options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions2
ms.date: 08/20/2024
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
  : public IUnknown
```

Additional options used to create WebView2 Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ExclusiveUserDataFolderAccess](#get_exclusiveuserdatafolderaccess) | Gets the `ExclusiveUserDataFolderAccess` property.
[put_ExclusiveUserDataFolderAccess](#put_exclusiveuserdatafolderaccess) | Whether other processes can create WebView2 from WebView2Environment created with the same user data folder and therefore sharing the same WebView browser process instance.

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

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions8> options8;
    if (options.As(&options8) == S_OK)
    {
        COREWEBVIEW2_SCROLLBAR_STYLE style = COREWEBVIEW2_SCROLLBAR_STYLE_FLUENT_OVERLAY;
        CHECK_FAILURE(options8->put_ScrollBarStyle(style));
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

Gets the `ExclusiveUserDataFolderAccess` property.

> public HRESULT [get_ExclusiveUserDataFolderAccess](#get_exclusiveuserdatafolderaccess)(BOOL * value)

#### put_ExclusiveUserDataFolderAccess

Whether other processes can create WebView2 from WebView2Environment created with the same user data folder and therefore sharing the same WebView browser process instance.

> public HRESULT [put_ExclusiveUserDataFolderAccess](#put_exclusiveuserdatafolderaccess)(BOOL value)

Default is FALSE.

