---
description: This is the ICoreWebView2 experimental interface for custom data partition.
title: WebView2 Win32 C++ ICoreWebView2Experimental20
ms.date: 07/25/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental20
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental20
- ICoreWebView2Experimental20.get_CustomDataPartitionId
- ICoreWebView2Experimental20.put_CustomDataPartitionId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental20

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental20
  : public IUnknown
```

This is the [ICoreWebView2](icorewebview2.md) experimental interface for custom data partition.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CustomDataPartitionId](#get_customdatapartitionid) | Gets the `CustomDataPartitionId` property.
[put_CustomDataPartitionId](#put_customdatapartitionid) | Sets the `CustomDataPartitionId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_CustomDataPartitionId

Gets the `CustomDataPartitionId` property.

> public HRESULT [get_CustomDataPartitionId](#get_customdatapartitionid)(LPWSTR * customDataPartitionId)

#### put_CustomDataPartitionId

Sets the `CustomDataPartitionId` property.

> public HRESULT [put_CustomDataPartitionId](#put_customdatapartitionid)(LPCWSTR customDataPartitionId)

This API requires enabling 2 experimental browser features to work properly. These features will be enabled by default in the future. Before these features are enabled by default, please enable them by ensuring `--enable-features=ThirdPartyStoragePartitioning,PartitionedCookies` is set in `AdditionalBrowserArguments` in `CoreWebView2EnvironmentOptions` used to create CoreWebView2Environment. If these features are not enabled, all data are treated as unpartitioned and stored in the global default location for the profile. When it is set, the page in the WebView will act as if the page were hosted in a top level site uniquely associated with the `customDataPartitionId` and have a separate storage partition as described in https://developer.chrome.com/docs/privacy-sandbox/storage-partitioning/ and separate cookie partition as described in https://developer.chrome.com/docs/privacy-sandbox/chips/ with all cookies partitioned. If `customDataPartitionId` is nullptr or empty string, the page inside the WebView will work normally with data treated as unpartitioned. The `customDataPartitionId` parameter is case sensitive. The default is an empty string. There is no restriction on the length or what characters can be used in partition id. The change of the custom data partition id will be applied to new page or iframe navigations and not impact existing pages and iframes. To avoid accidentally using the new partition id for new page or iframe navigations started by the old page, it is recommended to create a new WebView for new partition instead of changing partition. If you really have to change partition, it is recommended to navigate to a blank page before setting the new partition id and navigating to a page with the new partition.

As setting custom data partition id does not change DOM security model, developers should be very careful for WebViews with opener and opened window relationship, especially when the pages in the WebViews have same origin, like when the opened window is the same website or about:blank. The pages in these WebViews can access each other???s DOM and therefore can potentially access DOM storage and cookies in different partition for the same website. It is recommended to set the same custom data partition id for these WebViews, unless there is an absolute need to set different partition ids and only trusted code is hosted in them.

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

    Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalEnvironmentOptions> optionsExperimental;
    if (options.As(&optionsExperimental) == S_OK)
    {
        CHECK_FAILURE(optionsExperimental->put_AreBrowserExtensionsEnabled(TRUE));
    }

    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, m_userDataFolder.c_str(), options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
```

```cpp
    wil::com_ptr<ICoreWebView2Experimental20> webViewStaging20;
    webViewStaging20 = m_webView.try_query<ICoreWebView2Experimental20>();
    if (webViewStaging20)
    {
        wil::unique_cotaskmem_string partitionId;
        CHECK_FAILURE(webViewStaging20->get_CustomDataPartitionId(&partitionId));
        TextInputDialog dialog(
            m_appWindow->GetMainWindow(), L"Custom Datga Partition Id",
            L"Custom Datga Partition Id:",
            L"Enter data storage partition id, or leave blank to clear data storage "
            L"partition.",
            std::wstring(partitionId.get()));
        if (dialog.confirmed)
        {
            webViewStaging20->put_CustomDataPartitionId(dialog.input.c_str());
        }
    }
```

