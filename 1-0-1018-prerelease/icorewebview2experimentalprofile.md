---
description: Profile for ICoreWebView2Experimental8 interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile
---

# interface ICoreWebView2ExperimentalProfile

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile
  : public IUnknown
```

Profile for [ICoreWebView2Experimental8](icorewebview2experimental8.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled) | InPrivate mode is enabled or not.
[get_ProfileName](#get_profilename) | Name of the profile.
[get_ProfilePath](#get_profilepath) | Full path of the profile directory.

```cpp
        auto webview2Experimental8 = coreWebView2.try_query<ICoreWebView2Experimental8>();
        if (webview2Experimental8)
        {
            wil::com_ptr<ICoreWebView2ExperimentalProfile> profile;
            CHECK_FAILURE(webview2Experimental8->get_Profile(&profile));
            wil::unique_cotaskmem_string profile_path;
            CHECK_FAILURE(profile->get_ProfilePath(&profile_path));
            std::wstring str(profile_path.get());
            m_profileDirName = str.substr(str.find_last_of(L'\\') + 1);
            BOOL inPrivate = FALSE;
            CHECK_FAILURE(profile->get_IsInPrivateModeEnabled(&inPrivate));
            // update window title with m_profileDirName
            UpdateAppTitle();

            // update window icon
            SetAppIcon(inPrivate);
        }
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### get_IsInPrivateModeEnabled

InPrivate mode is enabled or not.

> public HRESULT [get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled)(BOOL * value)

#### get_ProfileName

Name of the profile.

> public HRESULT [get_ProfileName](#get_profilename)(LPWSTR * value)

#### get_ProfilePath

Full path of the profile directory.

> public HRESULT [get_ProfilePath](#get_profilepath)(LPWSTR * value)

