---
description: This is the ICoreWebView2Settings Experimental Interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings8
ms.date: 02/26/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings8
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSettings8
- ICoreWebView2ExperimentalSettings8.get_IsNonClientRegionSupportEnabled
- ICoreWebView2ExperimentalSettings8.put_IsNonClientRegionSupportEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSettings8

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings8
  : public IUnknown
```

This is the [ICoreWebView2Settings](icorewebview2settings.md) Experimental Interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsNonClientRegionSupportEnabled](#get_isnonclientregionsupportenabled) | The `IsNonClientRegionSupportEnabled` property enables web pages to use the `app-region` CSS style.
[put_IsNonClientRegionSupportEnabled](#put_isnonclientregionsupportenabled) | Set the IsNonClientRegionSupportEnabled property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_IsNonClientRegionSupportEnabled

The `IsNonClientRegionSupportEnabled` property enables web pages to use the `app-region` CSS style.

> public HRESULT [get_IsNonClientRegionSupportEnabled](#get_isnonclientregionsupportenabled)(BOOL * enabled)

Disabling/Enabling the `IsNonClientRegionSupportEnabled` takes effect after the next navigation. Defaults to `FALSE`.

When this property is `TRUE`, then all the non-client region features will be enabled: Draggable Regions will be enabled, they are regions on a webpage that are marked with the CSS attribute `app-region: drag/no-drag`. When set to `drag`, these regions will be treated like the window's title bar, supporting dragging of the entire WebView and its host app window; the system menu shows upon right click, and a double click will trigger maximizing/restoration of the window size.

When set to `FALSE`, all non-client region support will be disabled. The `app-region` CSS style will be ignored on web pages. 
```cpp
            BOOL nonClientRegionSupportEnabled;
            wil::com_ptr<ICoreWebView2ExperimentalSettings8> experimentalSettings;
            experimentalSettings = m_settings.try_query<ICoreWebView2ExperimentalSettings8>();
            CHECK_FEATURE_RETURN(experimentalSettings);

            CHECK_FAILURE(experimentalSettings->get_IsNonClientRegionSupportEnabled(
                &nonClientRegionSupportEnabled));
            if (nonClientRegionSupportEnabled)
            {
                CHECK_FAILURE(experimentalSettings->put_IsNonClientRegionSupportEnabled(FALSE));
                MessageBox(
                    nullptr,
                    L"Non-client region support will be disabled after the next navigation",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(experimentalSettings->put_IsNonClientRegionSupportEnabled(TRUE));
                MessageBox(
                    nullptr,
                    L"Non-client region support will be enabled after the next navigation",
                    L"Settings change", MB_OK);
            }
```

#### put_IsNonClientRegionSupportEnabled

Set the IsNonClientRegionSupportEnabled property.

> public HRESULT [put_IsNonClientRegionSupportEnabled](#put_isnonclientregionsupportenabled)(BOOL enabled)

