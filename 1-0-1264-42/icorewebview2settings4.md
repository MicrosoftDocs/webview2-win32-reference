---
description: A continuation of the ICoreWebView2Settings interface to manage autofill.
title: WebView2 Win32 C++ ICoreWebView2Settings4
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings4
---

# interface ICoreWebView2Settings4

```
interface ICoreWebView2Settings4
  : public ICoreWebView2Settings3
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md) interface to manage autofill.

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

This excludes password and credit card information. When IsGeneralAutofillEnabled is false, no suggestions appear, and no new information is saved. When IsGeneralAutofillEnabled is true, information is saved, suggestions appear and clicking on one will populate the form fields. It will apply immediately after setting. The default value is `TRUE`. This property is linked with `CoreWebView2Profile.IsGeneralAutofillEnabled`, so changing one will change the other. And all WebView2s that created with the same `CoreWebView2Profile` will share this property, so for the WebView2s with the same profile, their `CoreWebView2Settings.IsGeneralAutofillEnabled` and `CoreWebView2Profile.IsGeneralAutofillEnabled` are always in sync.

```cpp
            CHECK_FEATURE_RETURN(m_settings4);

            BOOL enabled;
            CHECK_FAILURE(m_settings4->get_IsGeneralAutofillEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(m_settings4->put_IsGeneralAutofillEnabled(FALSE));
                MessageBox(
                    nullptr, L"General autofill will be disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings4->put_IsGeneralAutofillEnabled(TRUE));
                MessageBox(
                    nullptr, L"General autofill will be enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### get_IsPasswordAutosaveEnabled

IsPasswordAutosaveEnabled controls whether autosave for password information is enabled.

> public HRESULT [get_IsPasswordAutosaveEnabled](#get_ispasswordautosaveenabled)(BOOL * value)

The IsPasswordAutosaveEnabled property behaves independently of the IsGeneralAutofillEnabled property. When IsPasswordAutosaveEnabled is false, no new password data is saved and no Save/Update Password prompts are displayed. However, if there was password data already saved before disabling this setting, then that password information is auto-populated, suggestions are shown and clicking on one will populate the fields. When IsPasswordAutosaveEnabled is true, password information is auto-populated, suggestions are shown and clicking on one will populate the fields, new data is saved, and a Save/Update Password prompt is displayed. It will apply immediately after setting. The default value is `FALSE`. This property is linked with `CoreWebView2Profile.IsPasswordAutosaveEnabled`, so changing one will change the other. And all WebView2s that created with the same `CoreWebView2Profile` will share this property, so for the WebView2s with the same profile, their `CoreWebView2Settings.IsPasswordAutosaveEnabled` and `CoreWebView2Profile.IsPasswordAutosaveEnabled` are always in sync.

```cpp
            CHECK_FEATURE_RETURN(m_settings4);

            BOOL enabled;
            CHECK_FAILURE(m_settings4->get_IsPasswordAutosaveEnabled(&enabled));
            if (enabled)
            {
                CHECK_FAILURE(m_settings4->put_IsPasswordAutosaveEnabled(FALSE));
                MessageBox(
                    nullptr, L"Password autosave will be disabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings4->put_IsPasswordAutosaveEnabled(TRUE));
                MessageBox(
                    nullptr, L"Password autosave will be enabled after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_IsGeneralAutofillEnabled

Set the IsGeneralAutofillEnabled property.

> public HRESULT [put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled)(BOOL value)

#### put_IsPasswordAutosaveEnabled

Set the IsPasswordAutosaveEnabled property.

> public HRESULT [put_IsPasswordAutosaveEnabled](#put_ispasswordautosaveenabled)(BOOL value)

