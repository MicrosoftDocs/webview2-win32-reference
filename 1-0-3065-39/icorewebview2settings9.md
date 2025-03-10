---
description: This is the ICoreWebView2Settings Experimental Interface.
title: WebView2 Win32 C++ ICoreWebView2Settings9
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings9
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings9
- ICoreWebView2Settings9.get_IsNonClientRegionSupportEnabled
- ICoreWebView2Settings9.put_IsNonClientRegionSupportEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings9

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Settings9
  : public ICoreWebView2Settings8
```

This is the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) Experimental Interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsNonClientRegionSupportEnabled](#get_isnonclientregionsupportenabled) | Gets the `IsNonClientRegionSupportEnabled` property.
[put_IsNonClientRegionSupportEnabled](#put_isnonclientregionsupportenabled) | The `IsNonClientRegionSupportEnabled` property enables web pages to use the `app-region` CSS style.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2420.47
WebView2 Win32 Prerelease |    1.0.2415

## Members

#### get_IsNonClientRegionSupportEnabled

Gets the `IsNonClientRegionSupportEnabled` property.

> public HRESULT [get_IsNonClientRegionSupportEnabled](#get_isnonclientregionsupportenabled)(BOOL * value)

#### put_IsNonClientRegionSupportEnabled

The `IsNonClientRegionSupportEnabled` property enables web pages to use the `app-region` CSS style.

> public HRESULT [put_IsNonClientRegionSupportEnabled](#put_isnonclientregionsupportenabled)(BOOL value)

Disabling/Enabling the `IsNonClientRegionSupportEnabled` takes effect after the next navigation. Defaults to `FALSE`.

When this property is `TRUE`, then all the non-client region features will be enabled: Draggable Regions will be enabled, they are regions on a webpage that are marked with the CSS attribute `app-region: drag/no-drag`. When set to `drag`, these regions will be treated like the window's title bar, supporting dragging of the entire WebView and its host app window; the system menu shows upon right click, and a double click will trigger maximizing/restoration of the window size.

When set to `FALSE`, all non-client region support will be disabled. The `app-region` CSS style will be ignored on web pages. 
```cpp
            BOOL nonClientRegionSupportEnabled;
            wil::com_ptr<ICoreWebView2Settings9> settings;
            settings = m_settings.try_query<ICoreWebView2Settings9>();
            CHECK_FEATURE_RETURN(settings);
            CHECK_FAILURE(
                settings->get_IsNonClientRegionSupportEnabled(&nonClientRegionSupportEnabled));
            if (nonClientRegionSupportEnabled)
            {
                CHECK_FAILURE(settings->put_IsNonClientRegionSupportEnabled(FALSE));
                MessageBox(
                    nullptr,
                    L"Non-client region support will be disabled after the next navigation",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(settings->put_IsNonClientRegionSupportEnabled(TRUE));
                MessageBox(
                    nullptr,
                    L"Non-client region support will be enabled after the next navigation",
                    L"Settings change", MB_OK);
            }
```

