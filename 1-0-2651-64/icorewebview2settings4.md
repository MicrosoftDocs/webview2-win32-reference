---
description: A continuation of the ICoreWebView2Settings interface to manage autofill.
title: WebView2 Win32 C++ ICoreWebView2Settings4
ms.date: 07/31/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings4
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings4
- ICoreWebView2Settings4.get_IsGeneralAutofillEnabled
- ICoreWebView2Settings4.get_IsPasswordAutosaveEnabled
- ICoreWebView2Settings4.put_IsGeneralAutofillEnabled
- ICoreWebView2Settings4.put_IsPasswordAutosaveEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings4

```
interface ICoreWebView2Settings4
  : public ICoreWebView2Settings3
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface to manage autofill.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled) | IsGeneralAutofillEnabled controls whether autofill for information like names, street and email addresses, phone numbers, and arbitrary input is enabled.
[get_IsPasswordAutosaveEnabled](#get_ispasswordautosaveenabled) | IsPasswordAutosaveEnabled controls whether autosave for password information is enabled.
[put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled) | Set the IsGeneralAutofillEnabled property.
[put_IsPasswordAutosaveEnabled](#put_ispasswordautosaveenabled) | Set the IsPasswordAutosaveEnabled property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_IsGeneralAutofillEnabled

IsGeneralAutofillEnabled controls whether autofill for information like names, street and email addresses, phone numbers, and arbitrary input is enabled.

> public HRESULT [get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled)(BOOL * value)

This excludes password and credit card information. When IsGeneralAutofillEnabled is false, no suggestions appear, and no new information is saved. When IsGeneralAutofillEnabled is true, information is saved, suggestions appear and clicking on one will populate the form fields. It will take effect immediately after setting. The default value is `TRUE`. This property has the same value as `CoreWebView2Profile.IsGeneralAutofillEnabled`, and changing one will change the other. All `CoreWebView2`s with the same `CoreWebView2Profile` will share the same value for this property, so for the `CoreWebView2`s with the same profile, their `CoreWebView2Settings.IsGeneralAutofillEnabled` and `CoreWebView2Profile.IsGeneralAutofillEnabled` will always have the same value.

```cpp
            CHECK_FEATURE_RETURN(m_settings4);

            BOOL enabled;
            CHECK_FAILURE(m_settings4->get_IsGeneralAutofillEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(m_settings4->put_IsGeneralAutofillEnabled(FALSE));
                MessageBox(
                    nullptr, L"General autofill will be disabled immediately.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings4->put_IsGeneralAutofillEnabled(TRUE));
                MessageBox(
                    nullptr, L"General autofill will be enabled immediately.",
                    L"Settings change", MB_OK);
            }
```

#### get_IsPasswordAutosaveEnabled

IsPasswordAutosaveEnabled controls whether autosave for password information is enabled.

> public HRESULT [get_IsPasswordAutosaveEnabled](#get_ispasswordautosaveenabled)(BOOL * value)

The IsPasswordAutosaveEnabled property behaves independently of the IsGeneralAutofillEnabled property. When IsPasswordAutosaveEnabled is false, no new password data is saved and no Save/Update Password prompts are displayed. However, if there was password data already saved before disabling this setting, then that password information is auto-populated, suggestions are shown and clicking on one will populate the fields. When IsPasswordAutosaveEnabled is true, password information is auto-populated, suggestions are shown and clicking on one will populate the fields, new data is saved, and a Save/Update Password prompt is displayed. It will take effect immediately after setting. The default value is `FALSE`. This property has the same value as `CoreWebView2Profile.IsPasswordAutosaveEnabled`, and changing one will change the other. All `CoreWebView2`s with the same `CoreWebView2Profile` will share the same value for this property, so for the `CoreWebView2`s with the same profile, their `CoreWebView2Settings.IsPasswordAutosaveEnabled` and `CoreWebView2Profile.IsPasswordAutosaveEnabled` will always have the same value.

```cpp
            CHECK_FEATURE_RETURN(m_settings4);

            BOOL enabled;
            CHECK_FAILURE(m_settings4->get_IsPasswordAutosaveEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(m_settings4->put_IsPasswordAutosaveEnabled(FALSE));
                MessageBox(
                    nullptr, L"Password autosave will be disabled immediately.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings4->put_IsPasswordAutosaveEnabled(TRUE));
                MessageBox(
                    nullptr, L"Password autosave will be enabled immediately.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsGeneralAutofillEnabled

Set the IsGeneralAutofillEnabled property.

> public HRESULT [put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled)(BOOL value)

#### put_IsPasswordAutosaveEnabled

Set the IsPasswordAutosaveEnabled property.

> public HRESULT [put_IsPasswordAutosaveEnabled](#put_ispasswordautosaveenabled)(BOOL value)

