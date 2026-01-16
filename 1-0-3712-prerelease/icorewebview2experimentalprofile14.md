---
description: This is the ICoreWebView2Profile interface for PageInteractionRestrictionManager allowlist management.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile14
ms.date: 12/02/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile14
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile14
- ICoreWebView2ExperimentalProfile14.SetPageInteractionRestrictionManagerAllowList
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile14

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile14
  : public IUnknown
```

This is the [ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) interface for PageInteractionRestrictionManager allowlist management.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[SetPageInteractionRestrictionManagerAllowList](#setpageinteractionrestrictionmanagerallowlist) | Sets the allowlist of URLs that are allowed to access the PageInteractionRestrictionManager API.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3590

## Members

#### SetPageInteractionRestrictionManagerAllowList

Sets the allowlist of URLs that are allowed to access the PageInteractionRestrictionManager API.

> public HRESULT [SetPageInteractionRestrictionManagerAllowList](#setpageinteractionrestrictionmanagerallowlist)(UINT32 allowlistCount, LPCWSTR * allowlist)

This method configures an allowlist of URLs that determines which web pages can use the PageInteractionRestrictionManager API. Only URLs that match entries in this allowlist (either exact matches or wildcard patterns) will have access to the PageInteractionRestrictionManager functionality.

URL Matching Logic: The allowlist accepts both exact URL strings and wildcard patterns. For wildcard patterns, `*` matches zero or more characters.

For detailed URL matching examples, refer to the table at [`AddWebResourceRequestedFilter`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.web.webview2.core.corewebview2.addwebresourcerequestedfilter). 
```cpp
    auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
    if (!webView2_13)
    {
        return E_NOINTERFACE;
    }

    wil::com_ptr<ICoreWebView2Profile> webView2Profile;
    HRESULT hr = webView2_13->get_Profile(&webView2Profile);
    if (FAILED(hr))
    {
        return hr;
    }

    auto experimentalProfile14 =
        webView2Profile.try_query<ICoreWebView2ExperimentalProfile14>();
    if (!experimentalProfile14)
    {
        return E_NOINTERFACE;
    }

    // allowlist consists of URL patterns that can access PageInteractionRestrictionManager API
    // Examples: "https://example.com/*", "https://*.trusted-domain.com/*", "*://site.com/*"
    return experimentalProfile14->SetPageInteractionRestrictionManagerAllowList(
        static_cast<UINT32>(allowlist.size()), allowlist.data());
```

