---
description: Interfaces in profile for managing password-autosave and general-autofill.
title: WebView2 Win32 C++ ICoreWebView2Profile6
ms.date: 01/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile6
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile6
- ICoreWebView2Profile6.get_IsGeneralAutofillEnabled
- ICoreWebView2Profile6.get_IsPasswordAutosaveEnabled
- ICoreWebView2Profile6.put_IsGeneralAutofillEnabled
- ICoreWebView2Profile6.put_IsPasswordAutosaveEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile6

```
interface ICoreWebView2Profile6
  : public ICoreWebView2Profile5
```

Interfaces in profile for managing password-autosave and general-autofill.

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
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1829

## Members

#### get_IsGeneralAutofillEnabled

IsGeneralAutofillEnabled controls whether autofill for information like names, street and email addresses, phone numbers, and arbitrary input is enabled.

> public HRESULT [get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled)(BOOL * value)

This excludes password and credit card information. When IsGeneralAutofillEnabled is false, no suggestions appear, and no new information is saved. When IsGeneralAutofillEnabled is true, information is saved, suggestions appear and clicking on one will populate the form fields. It will take effect immediately after setting. The default value is `TRUE`. This property has the same value as `CoreWebView2Settings.IsGeneralAutofillEnabled`, and changing one will change the other. All `CoreWebView2`s with the same `CoreWebView2Profile` will share the same value for this property, so for the `CoreWebView2`s with the same profile, their `CoreWebView2Settings.IsGeneralAutofillEnabled` and `CoreWebView2Profile.IsGeneralAutofillEnabled` will always have the same value.

```cpp
            // Get the profile object.
            auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
            CHECK_FEATURE_RETURN(webView2_13);
            wil::com_ptr<ICoreWebView2Profile> webView2Profile;
            CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
            CHECK_FEATURE_RETURN(webView2Profile);
            auto webView2Profile6 = webView2Profile.try_query<ICoreWebView2Profile6>();
            CHECK_FEATURE_RETURN(webView2Profile6);

            BOOL enabled;
            CHECK_FAILURE(webView2Profile6->get_IsGeneralAutofillEnabled(&enabled));
            // Set general-autofill property to the opposite value to current value.
            if (enabled)
            {
                CHECK_FAILURE(webView2Profile6->put_IsGeneralAutofillEnabled(FALSE));
                MessageBox(
                    nullptr,
                    L"General autofill will be disabled immediately in all WebView2 with the "
                    L"same profile.",
                    L"Profile settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(webView2Profile6->put_IsGeneralAutofillEnabled(TRUE));
                MessageBox(
                    nullptr,
                    L"General autofill will be enabled immediately in all WebView2 with the "
                    L"same profile.",
                    L"Profile settings change", MB_OK);
            }
```

#### get_IsPasswordAutosaveEnabled

IsPasswordAutosaveEnabled controls whether autosave for password information is enabled.

> public HRESULT [get_IsPasswordAutosaveEnabled](#get_ispasswordautosaveenabled)(BOOL * value)

The IsPasswordAutosaveEnabled property behaves independently of the IsGeneralAutofillEnabled property. When IsPasswordAutosaveEnabled is false, no new password data is saved and no Save/Update Password prompts are displayed. However, if there was password data already saved before disabling this setting, then that password information is auto-populated, suggestions are shown and clicking on one will populate the fields. When IsPasswordAutosaveEnabled is true, password information is auto-populated, suggestions are shown and clicking on one will populate the fields, new data is saved, and a Save/Update Password prompt is displayed. It will take effect immediately after setting. The default value is `FALSE`. This property has the same value as `CoreWebView2Settings.IsPasswordAutosaveEnabled`, and changing one will change the other. All `CoreWebView2`s with the same `CoreWebView2Profile` will share the same value for this property, so for the `CoreWebView2`s with the same profile, their `CoreWebView2Settings.IsPasswordAutosaveEnabled` and `CoreWebView2Profile.IsPasswordAutosaveEnabled` will always have the same value.

```cpp
            // Get the profile object.
            auto webView2_13 = m_webView.try_query<ICoreWebView2_13>();
            CHECK_FEATURE_RETURN(webView2_13);
            wil::com_ptr<ICoreWebView2Profile> webView2Profile;
            CHECK_FAILURE(webView2_13->get_Profile(&webView2Profile));
            CHECK_FEATURE_RETURN(webView2Profile);
            auto webView2Profile6 = webView2Profile.try_query<ICoreWebView2Profile6>();
            CHECK_FEATURE_RETURN(webView2Profile6);

            BOOL enabled;
            CHECK_FAILURE(webView2Profile6->get_IsPasswordAutosaveEnabled(&enabled));
            // Set password-autosave property to the opposite value to current value.
            if (enabled)
            {
                CHECK_FAILURE(webView2Profile6->put_IsPasswordAutosaveEnabled(FALSE));
                MessageBox(
                    nullptr,
                    L"Password autosave will be disabled immediately in all "
                    L"WebView2 with the same profile.",
                    L"Profile settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(webView2Profile6->put_IsPasswordAutosaveEnabled(TRUE));
                MessageBox(
                    nullptr,
                    L"Password autosave will be enabled immediately in all "
                    L"WebView2 with the same profile.",
                    L"Profile settings change", MB_OK);
            }
```

#### put_IsGeneralAutofillEnabled

Set the IsGeneralAutofillEnabled property.

> public HRESULT [put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled)(BOOL value)

#### put_IsPasswordAutosaveEnabled

Set the IsPasswordAutosaveEnabled property.

> public HRESULT [put_IsPasswordAutosaveEnabled](#put_ispasswordautosaveenabled)(BOOL value)

