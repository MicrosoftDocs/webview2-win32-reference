---
description: This is the interface in ControllerOptions for LocaleRegion.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalControllerOptions
ms.date: 01/13/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalControllerOptions
---

# interface ICoreWebView2ExperimentalControllerOptions

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalControllerOptions
  : public IUnknown
```

This is the interface in ControllerOptions for LocaleRegion.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_LocaleRegion](#get_localeregion) | Interface for locale region that is updated through the ControllerOptions API.
[put_LocaleRegion](#put_localeregion) | Sets the `LocaleRegion` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### get_LocaleRegion

Interface for locale region that is updated through the ControllerOptions API.

> public HRESULT [get_LocaleRegion](#get_localeregion)(LPWSTR * locale)

The default region for the WebView2. It applies to JavaScript API Intl.DateTimeFormat() which affects string formatting like in the time/date formats. The intended locale value is in the format of `language[-country]` where `language` is the 2-letter code from [ISO 639](https://www.iso.org/iso-639-language-codes.html) and `country` is the 2-letter code from [ISO 3166](https://www.iso.org/standard/72482.html).

This property will update the environment creation. This is global and immutable, so changes will not be reflected in the existing webviews. They will need to be closed and reopened in order to see the changes reflected from using the new creation environment.

Validation is done on the V8 engine to match on the closest locale from the passed in locale region value. For example, passing in "en_gb" will reflect the "en-GB" locale in V8. If V8 cannot find any matching locale on the input value, it will default to the WebView2 language as the locale.

The default value for LocaleRegion will be depend on the WebView2 language and OS region. If the language portions of the WebView2 language and OS Region match, then it will use the OS region. Otherwise, it will use the WebView2 language. 
**OS Region**|**WebView2 Language**|**Default WebView2 LocaleRegion**
--------- | --------- | ---------
en-GB   |en-US   |en-GB
es-MX   |en-US   |en-US
en-US   |en-GB   |en-US
The default value can be reset using the empty string.

Use OS specific APIs to determine the OS region to use with this property if you want to always match the OS. For example, in Windows you can use the GetLocaleInfoEx() API. 
```cpp
int LanguageCodeBufferSize =
    ::GetLocaleInfoEx(LOCALE_NAME_USER_DEFAULT, LOCALE_SNAME, nullptr, 0);
std::unique_ptr<char[]> buffer(new char[LanguageCodeBufferSize]);
WCHAR* w_language_code = new WCHAR[LanguageCodeBufferSize];
::GetLocaleInfoEx(LOCALE_NAME_USER_DEFAULT, LOCALE_SNAME, w_language_code,
                  LanguageCodeBufferSize);
wcstombs(buffer.get(), w_language_code, LanguageCodeBufferSize);
delete[] w_language_code;
return buffer;
```

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings). 
```cpp
    wil::com_ptr<ICoreWebView2ExperimentalControllerOptions>
        webView2ExperimentalControllerOptions;
    if (SUCCEEDED(
            options->QueryInterface(IID_PPV_ARGS(&webView2ExperimentalControllerOptions))))
    {
        if (m_webviewOption.useOSRegion)
        {
            int languageCodeSize =
                GetLocaleInfoEx(LOCALE_NAME_USER_DEFAULT, LOCALE_SNAME, nullptr, 0);
            WCHAR* osLocale = new WCHAR[languageCodeSize];
            GetLocaleInfoEx(LOCALE_NAME_USER_DEFAULT, LOCALE_SNAME, osLocale, languageCodeSize);
            CHECK_FAILURE(webView2ExperimentalControllerOptions->put_LocaleRegion(osLocale));
        }
        else if (!m_webviewOption.localeRegion.empty())
        {
            CHECK_FAILURE(webView2ExperimentalControllerOptions->put_LocaleRegion(
                m_webviewOption.localeRegion.c_str()));
        }
    }
```

#### put_LocaleRegion

Sets the `LocaleRegion` property.

> public HRESULT [put_LocaleRegion](#put_localeregion)(LPCWSTR locale)

