---
description: This is the ICoreWebView2ExperimentalEnvironmentOptions interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironmentOptions
ms.date: 10/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironmentOptions
---

# interface ICoreWebView2ExperimentalEnvironmentOptions

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironmentOptions
  : public IUnknown
```

This is the ICoreWebView2ExperimentalEnvironmentOptions interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetCustomSchemeRegistrations](#getcustomschemeregistrations) | Array of custom scheme registrations.
[SetCustomSchemeRegistrations](#setcustomschemeregistrations) | Set the array of custom scheme registrations to be used.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.579

## Members

#### GetCustomSchemeRegistrations

Array of custom scheme registrations.

> public HRESULT [GetCustomSchemeRegistrations](#getcustomschemeregistrations)(UINT32 * count, [ICoreWebView2ExperimentalCustomSchemeRegistration](icorewebview2experimentalcustomschemeregistration.md) *** schemeRegistrations)

The returned ICoreWebView2CustomSchemeRegistration pointers must be released, and the array itself must be deallocated with CoTaskMemFree.

#### SetCustomSchemeRegistrations

Set the array of custom scheme registrations to be used.

> public HRESULT [SetCustomSchemeRegistrations](#setcustomschemeregistrations)(UINT32 count, [ICoreWebView2ExperimentalCustomSchemeRegistration](icorewebview2experimentalcustomschemeregistration.md) ** schemeRegistrations)

```cpp
    Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalEnvironmentOptions> optionsExperimental;
    if (options.As(&optionsExperimental) == S_OK)
    {
        const WCHAR* allowedOrigins[1] = {L"https://*.example.com"};

        auto customSchemeRegistration =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"custom-scheme");
        customSchemeRegistration->SetAllowedOrigins(1, allowedOrigins);
        auto customSchemeRegistration2 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"wv2rocks");
        customSchemeRegistration2->put_TreatAsSecure(TRUE);
        customSchemeRegistration2->SetAllowedOrigins(1, allowedOrigins);
        auto customSchemeRegistration3 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(
                L"custom-scheme-not-in-allowed-origins");
        ICoreWebView2ExperimentalCustomSchemeRegistration* registrations[3] = {
            customSchemeRegistration.Get(), customSchemeRegistration2.Get(),
            customSchemeRegistration3.Get()};
        optionsExperimental->SetCustomSchemeRegistrations(
            2, static_cast<ICoreWebView2ExperimentalCustomSchemeRegistration**>(registrations));
    }
```

