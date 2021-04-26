---
description: This is an extension of the ICoreWebView2Settings Experimental interface to manage auto fill.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings3
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 04/23/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings3
---

# interface ICoreWebView2ExperimentalSettings3

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings3
  : public IUnknown
```

This is an extension of the [ICoreWebView2Settings](icorewebview2settings.md) Experimental interface to manage auto fill.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled) | IsGeneralAutofillEnabled controls whether autofill for information like names, street and email addresses, phone numbers, and aribtrary input is enabled.
[get_IsPasswordAutofillEnabled](#get_ispasswordautofillenabled) | IsPasswordAutofillEnabled controls whether autofill for password information is enabled.
[put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled) | Set the IsGeneralAutofillEnabled property.
[put_IsPasswordAutofillEnabled](#put_ispasswordautofillenabled) | Set the IsPasswordAutofillEnabled property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### get_IsGeneralAutofillEnabled

IsGeneralAutofillEnabled controls whether autofill for information like names, street and email addresses, phone numbers, and aribtrary input is enabled.

> public HRESULT [get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled)(BOOL * isGeneralAutofillEnabled)

This excludes password information. When isGeneralAutofillEnabled is false, no suggestions appear, and no new information is saved. When isGeneralAutofillEnabled is true, information is saved, suggestions appear and clicking on one will populate the form fields. The default value is `TRUE`.

```cpp
            wil::com_ptr<ICoreWebView2ExperimentalSettings3> experimental_settings3;
            experimental_settings3 = m_settings.try_query<ICoreWebView2ExperimentalSettings3>();
            CHECK_FEATURE_RETURN(experimental_settings3);

                BOOL enabled;
                CHECK_FAILURE(experimental_settings3->get_IsGeneralAutofillEnabled(&enabled));
                if (enabled)
                {
                    CHECK_FAILURE(experimental_settings3->put_IsGeneralAutofillEnabled(FALSE));
                    MessageBox(
                        nullptr, L"General autofill will be disabled after the next navigation.",
                        L"Settings change", MB_OK);
                }
                else
                {
                    CHECK_FAILURE(experimental_settings3->put_IsGeneralAutofillEnabled(TRUE));
                    MessageBox(
                        nullptr, L"General autofill will be enabled after the next navigation.",
                        L"Settings change", MB_OK);
                }
```

#### get_IsPasswordAutofillEnabled

IsPasswordAutofillEnabled controls whether autofill for password information is enabled.

> public HRESULT [get_IsPasswordAutofillEnabled](#get_ispasswordautofillenabled)(BOOL * isPasswordAutofillEnabled)

The isPasswordAutofillEnabled property behaves independently of the isGeneralAutofillEnabled property. When isPasswordAutofillEnabled is false, no new password data is saved and no Save/Update Password prompts are displayed. However, if there was password data already saved before disabling this setting, then that password information is auto-populated, suggestions are shown and clicking on one will populate the fields. When isPasswordAutofillEnabled is true, password information is auto-populated, suggestions are shown and clicking on one will populate the fields, new data is saved, and a Save/Update Password prompt is displayed. The default value is `FALSE`.

```cpp
            wil::com_ptr<ICoreWebView2ExperimentalSettings3> experimental_settings3;
            experimental_settings3 = m_settings.try_query<ICoreWebView2ExperimentalSettings3>();
            CHECK_FEATURE_RETURN(experimental_settings3);
            BOOL enabled;
            CHECK_FAILURE(experimental_settings3->get_IsPasswordAutofillEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(experimental_settings3->put_IsPasswordAutofillEnabled(FALSE));
                MessageBox(
                    nullptr,
                    L"Password autofill will be disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(experimental_settings3->put_IsPasswordAutofillEnabled(TRUE));
                MessageBox(
                    nullptr,
                    L"Password autofill will be enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsGeneralAutofillEnabled

Set the IsGeneralAutofillEnabled property.

> public HRESULT [put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled)(BOOL isGeneralAutofillEnabled)

#### put_IsPasswordAutofillEnabled

Set the IsPasswordAutofillEnabled property.

> public HRESULT [put_IsPasswordAutofillEnabled](#put_ispasswordautofillenabled)(BOOL isPasswordAutofillEnabled)

