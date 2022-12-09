---
description: This is the ICoreWebView2 experimental profile.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile5
ms.date: 12/09/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile5
---

# interface ICoreWebView2ExperimentalProfile5

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile5
  : public IUnknown
```

This is the [ICoreWebView2](icorewebview2.md) experimental profile.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_PreferredTrackingPreventionLevel](#get_preferredtrackingpreventionlevel) | The `PreferredTrackingPreventionLevel` property allows you to control levels of tracking prevention for WebView2 which are associated with a profile.
[put_PreferredTrackingPreventionLevel](#put_preferredtrackingpreventionlevel) | Set the `PreferredTrackingPreventionLevel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_PreferredTrackingPreventionLevel

The `PreferredTrackingPreventionLevel` property allows you to control levels of tracking prevention for WebView2 which are associated with a profile.

> public HRESULT [get_PreferredTrackingPreventionLevel](#get_preferredtrackingpreventionlevel)(COREWEBVIEW2_TRACKING_PREVENTION_LEVEL * value)

This level would apply to the context of the profile. That is, all WebView2s sharing the same profile will be affected and also the value is persisted in the user data folder.

See `COREWEBVIEW2_TRACKING_PREVENTION_LEVEL` for descriptions of levels.

If tracking prevention feature is enabled when creating the WebView2 environment, you can also disable tracking prevention later using this property and `COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_NONE` value but that doesn't improves runtime performance.

There is `ICoreWebView2ExperimentalEnvironmentOptions2::EnableTrackingPrevention` property to enable/disable tracking prevention feature for all the WebView2's created in the same environment. If enabled, `PreferredTrackingPreventionLevel` is set to `COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BALANCED` by default for all the WebView2's and profiles created in the same environment or is set to the level whatever value was last changed/persisted to the profile. If disabled `PreferredTrackingPreventionLevel` is not respected by WebView2. If `PreferredTrackingPreventionLevel` is set when the feature is disabled, the property value get changed and persisted but it will takes effect only if `ICoreWebView2ExperimentalEnvironmentOptions2::EnableTrackingPrevention` is true.

See `ICoreWebView2ExperimentalEnvironmentOptions2::EnableTrackingPrevention` for more details. 
```cpp
void SettingsComponent::SetTrackingPreventionLevel(COREWEBVIEW2_TRACKING_PREVENTION_LEVEL value)
{
    wil::com_ptr<ICoreWebView2_13> webView2_13;
    webView2_13 = m_webView.try_query<ICoreWebView2_13>();

    if (webView2_13)
    {
        wil::com_ptr<ICoreWebView2Profile> profile;
        CHECK_FAILURE(webView2_13->get_Profile(&profile));

        auto profileExperimental5 = profile.try_query<ICoreWebView2ExperimentalProfile5>();
        if (profileExperimental5)
        {
            CHECK_FAILURE(profileExperimental5->put_PreferredTrackingPreventionLevel(value));
            MessageBox(
                nullptr, L"Tracking prevention level is set successfully",
                L"Tracking Prevention Level", MB_OK);
        }
    }
}
```

#### put_PreferredTrackingPreventionLevel

Set the `PreferredTrackingPreventionLevel` property.

> public HRESULT [put_PreferredTrackingPreventionLevel](#put_preferredtrackingpreventionlevel)(COREWEBVIEW2_TRACKING_PREVENTION_LEVEL value)

If `ICoreWebView2ExperimentalEnvironmentOptions2::EnableTrackingPrevention` is false, this property will be changed and persisted to the profile but the WebView2 ignores the level silently.

