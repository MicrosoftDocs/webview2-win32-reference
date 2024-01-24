---
description: Used to get ICoreWebView2ExperimentalProfile object.
title: WebView2 Win32 C++ ICoreWebView2Experimental8
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 10/28/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental8
---

# interface ICoreWebView2Experimental8

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental8
  : public IUnknown
```

Used to get [ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Profile](#get_profile) | The associated [ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) object.

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

#### get_Profile

The associated [ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) object.

> public HRESULT [get_Profile](#get_profile)([ICoreWebView2ExperimentalProfile](icorewebview2experimentalprofile.md) ** value)

