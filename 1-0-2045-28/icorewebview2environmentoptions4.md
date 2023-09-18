---
description: Additional options used to create WebView2 Environment that manages custom scheme registration.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions4
ms.date: 09/18/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions4
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions4
- ICoreWebView2EnvironmentOptions4.GetCustomSchemeRegistrations
- ICoreWebView2EnvironmentOptions4.SetCustomSchemeRegistrations
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions4

```
interface ICoreWebView2EnvironmentOptions4
  : public IUnknown
```

Additional options used to create WebView2 Environment that manages custom scheme registration.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetCustomSchemeRegistrations](#getcustomschemeregistrations) | Array of custom scheme registrations.
[SetCustomSchemeRegistrations](#setcustomschemeregistrations) | Set the array of custom scheme registrations to be used.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1587.40
WebView2 Win32 Prerelease |    1.0.1619

## Members

#### GetCustomSchemeRegistrations

Array of custom scheme registrations.

> public HRESULT [GetCustomSchemeRegistrations](#getcustomschemeregistrations)(UINT32 * count, [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md) *** schemeRegistrations)

The returned [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md) pointers must be released, and the array itself must be deallocated with CoTaskMemFree.

#### SetCustomSchemeRegistrations

Set the array of custom scheme registrations to be used.

> public HRESULT [SetCustomSchemeRegistrations](#setcustomschemeregistrations)(UINT32 count, [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md) ** schemeRegistrations)

```cpp
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
```

