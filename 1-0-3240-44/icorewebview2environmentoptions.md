---
description: Options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions
- ICoreWebView2EnvironmentOptions.get_AdditionalBrowserArguments
- ICoreWebView2EnvironmentOptions.get_AllowSingleSignOnUsingOSPrimaryAccount
- ICoreWebView2EnvironmentOptions.get_Language
- ICoreWebView2EnvironmentOptions.get_TargetCompatibleBrowserVersion
- ICoreWebView2EnvironmentOptions.put_AdditionalBrowserArguments
- ICoreWebView2EnvironmentOptions.put_AllowSingleSignOnUsingOSPrimaryAccount
- ICoreWebView2EnvironmentOptions.put_Language
- ICoreWebView2EnvironmentOptions.put_TargetCompatibleBrowserVersion
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2EnvironmentOptions
  : public IUnknown
```

Options used to create WebView2 Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalBrowserArguments](#get_additionalbrowserarguments) | Changes the behavior of the WebView.
[get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount) | The `AllowSingleSignOnUsingOSPrimaryAccount` property is used to enable single sign on with Azure Active Directory (AAD) and personal Microsoft Account (MSA) resources inside WebView.
[get_Language](#get_language) | The default display language for WebView.
[get_TargetCompatibleBrowserVersion](#get_targetcompatiblebrowserversion) | Specifies the version of the WebView2 Runtime binaries required to be compatible with your app.
[put_AdditionalBrowserArguments](#put_additionalbrowserarguments) | Sets the `AdditionalBrowserArguments` property.
[put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount) | Sets the `AllowSingleSignOnUsingOSPrimaryAccount` property.
[put_Language](#put_language) | Sets the `Language` property.
[put_TargetCompatibleBrowserVersion](#put_targetcompatiblebrowserversion) | Sets the `TargetCompatibleBrowserVersion` property.

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
WebView2 Win32            |    0.9.488
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_AdditionalBrowserArguments

Changes the behavior of the WebView.

> public HRESULT [get_AdditionalBrowserArguments](#get_additionalbrowserarguments)(LPWSTR * value)

The arguments are passed to the browser process as part of the command. For more information about using command-line switches with Chromium browser processes, navigate to [Run Chromium with Flags](https://www.chromium.org/developers/how-tos/run-chromium-with-flags). The value appended to a switch is appended to the browser process, for example, in `--edge-webview-switches=xxx` the value is `xxx`. If you specify a switch that is important to WebView functionality, it is ignored, for example, `--user-data-dir`. Specific features are disabled internally and blocked from being enabled. If a switch is specified multiple times, only the last instance is used.

> [!NOTE]
> A merge of the different values of the same switch is not attempted, except for disabled and enabled features. The features specified by `--enable-features` and `--disable-features` are merged with simple logic.
> * The features is the union of the specified features and built-in features. If a feature is disabled, it is removed from the enabled features list.

If you specify command-line switches and use the `additionalBrowserArguments` parameter, the `--edge-webview-switches` value takes precedence and is processed last. If a switch fails to parse, the switch is ignored. The default state for the operation is to run the browser process with no extra flags.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_AllowSingleSignOnUsingOSPrimaryAccount

The `AllowSingleSignOnUsingOSPrimaryAccount` property is used to enable single sign on with Azure Active Directory (AAD) and personal Microsoft Account (MSA) resources inside WebView.

> public HRESULT [get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount)(BOOL * allow)

All AAD accounts, connected to Windows and shared for all apps, are supported. For MSA, SSO is only enabled for the account associated for Windows account login, if any. Default is disabled. Universal Windows Platform apps must also declare `enterpriseCloudSSO`[Restricted capabilities](/windows/uwp/packaging/app-capability-declarations\#restricted-capabilities) for the single sign on (SSO) to work.

#### get_Language

The default display language for WebView.

> public HRESULT [get_Language](#get_language)(LPWSTR * value)

It applies to browser UI such as context menu and dialogs. It also applies to the `accept-languages` HTTP header that WebView sends to websites. The intended locale value is in the format of BCP 47 Language Tags. More information can be found from [IETF BCP47](https://www.ietf.org/rfc/bcp/bcp47.html).

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_TargetCompatibleBrowserVersion

Specifies the version of the WebView2 Runtime binaries required to be compatible with your app.

> public HRESULT [get_TargetCompatibleBrowserVersion](#get_targetcompatiblebrowserversion)(LPWSTR * value)

This defaults to the WebView2 Runtime version that corresponds with the version of the SDK the app is using. The format of this value is the same as the format of the `BrowserVersionString` property and other `BrowserVersion` values. Only the version part of the `BrowserVersion` value is respected. The channel suffix, if it exists, is ignored. The version of the WebView2 Runtime binaries actually used may be different from the specified `TargetCompatibleBrowserVersion`. The binaries are only guaranteed to be compatible. Verify the actual version on the `BrowserVersionString` property on the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment).

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_AdditionalBrowserArguments

Sets the `AdditionalBrowserArguments` property.

> public HRESULT [put_AdditionalBrowserArguments](#put_additionalbrowserarguments)(LPCWSTR value)

Please note that calling this API twice will replace the previous value rather than appending to it. If there are multiple switches, there should be a space in between them. The one exception is if multiple features are being enabled/disabled for a single switch, in which case the features should be comma-seperated. Ex. "--disable-features=feature1,feature2 --some-other-switch --do-something"

#### put_AllowSingleSignOnUsingOSPrimaryAccount

Sets the `AllowSingleSignOnUsingOSPrimaryAccount` property.

> public HRESULT [put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount)(BOOL allow)

#### put_Language

Sets the `Language` property.

> public HRESULT [put_Language](#put_language)(LPCWSTR value)

#### put_TargetCompatibleBrowserVersion

Sets the `TargetCompatibleBrowserVersion` property.

> public HRESULT [put_TargetCompatibleBrowserVersion](#put_targetcompatiblebrowserversion)(LPCWSTR value)

