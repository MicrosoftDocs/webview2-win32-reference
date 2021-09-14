---
description: This is an extension of the ICoreWebView2Settings Experimental interface for IsSwipeNavigationEnabled.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings5
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings5
---

# interface ICoreWebView2ExperimentalSettings5

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings5
  : public IUnknown
```

This is an extension of the [ICoreWebView2Settings](icorewebview2settings.md) Experimental interface for IsSwipeNavigationEnabled.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSwipeNavigationEnabled](#get_isswipenavigationenabled) | The `IsSwipeNavigationEnabled` property enables or disables the ability of the end user to use swiping gesture on touch input enabled devices to navigate in WebView2.
[put_IsSwipeNavigationEnabled](#put_isswipenavigationenabled) | Set the `IsSwipeNavigationEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_IsSwipeNavigationEnabled

The `IsSwipeNavigationEnabled` property enables or disables the ability of the end user to use swiping gesture on touch input enabled devices to navigate in WebView2.

> public HRESULT [get_IsSwipeNavigationEnabled](#get_isswipenavigationenabled)(BOOL * enabled)

Swiping gesture navigation on touch screen includes:

1. Swipe left/right (swipe horizontally) to navigate to previous/next page in navigation history.

1. Pull to refresh (swipe vertically) the current page. (This feature is currently disabled by default in the browser, to enable in WebView2, use `put_AdditionalBrowserArguments` api with "--pull-to-refresh" switch). It defaults to `TRUE`. When set to `FALSE`, the end user cannot swipe to navigate or pull to refresh. This API only affects the overscrolling navigation functionality and has no effect on the scrolling interaction used to explore the web content shown in WebView2.

```cpp
            CHECK_FEATURE_RETURN(m_experimentalSettings5);
            BOOL swipeNavigationEnabled;
            CHECK_FAILURE(
                m_experimentalSettings5->get_IsSwipeNavigationEnabled(&swipeNavigationEnabled));
            if (swipeNavigationEnabled)
            {
                CHECK_FAILURE(m_experimentalSettings5->put_IsSwipeNavigationEnabled(FALSE));
                MessageBox(
                    nullptr, L"Swipe to navigate is enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsSwipeNavigationEnabled

Set the `IsSwipeNavigationEnabled` property.

> public HRESULT [put_IsSwipeNavigationEnabled](#put_isswipenavigationenabled)(BOOL enabled)

