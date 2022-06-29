---
description: A continuation of the ICoreWebView2Settings interface to manage swipe navigation.
title: WebView2 Win32 C++ ICoreWebView2Settings6
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings6
---

# interface ICoreWebView2Settings6

```
interface ICoreWebView2Settings6
  : public ICoreWebView2Settings5
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md) interface to manage swipe navigation.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSwipeNavigationEnabled](#get_isswipenavigationenabled) | The `IsSwipeNavigationEnabled` property enables or disables the ability of the end user to use swiping gesture on touch input enabled devices to navigate in WebView2.
[put_IsSwipeNavigationEnabled](#put_isswipenavigationenabled) | Set the `IsSwipeNavigationEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_IsSwipeNavigationEnabled

The `IsSwipeNavigationEnabled` property enables or disables the ability of the end user to use swiping gesture on touch input enabled devices to navigate in WebView2.

> public HRESULT [get_IsSwipeNavigationEnabled](#get_isswipenavigationenabled)(BOOL * enabled)

It defaults to `TRUE`.

When this property is `TRUE`, then all configured navigation gestures are enabled:

1. Swiping left and right to navigate forward and backward is always configured.

1. Swiping down to refresh is off by default and not exposed via our API currently, it requires the "--pull-to-refresh" option to be included in the additional browser arguments to be configured. (See put_AdditionalBrowserArguments.)

When set to `FALSE`, the end user cannot swipe to navigate or pull to refresh. This API only affects the overscrolling navigation functionality and has no effect on the scrolling interaction used to explore the web content shown in WebView2.

Disabling/Enabling IsSwipeNavigationEnabled takes effect after the next navigation.

```cpp
            CHECK_FEATURE_RETURN(m_settings6);
            BOOL swipeNavigationEnabled;
            CHECK_FAILURE(m_settings6->get_IsSwipeNavigationEnabled(&swipeNavigationEnabled));
            if (swipeNavigationEnabled)
            {
                CHECK_FAILURE(m_settings6->put_IsSwipeNavigationEnabled(FALSE));
                MessageBox(
                    nullptr, L"Swipe to navigate is disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings6->put_IsSwipeNavigationEnabled(TRUE));
                MessageBox(
                    nullptr, L"Swipe to navigate is enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsSwipeNavigationEnabled

Set the `IsSwipeNavigationEnabled` property.

> public HRESULT [put_IsSwipeNavigationEnabled](#put_isswipenavigationenabled)(BOOL enabled)

