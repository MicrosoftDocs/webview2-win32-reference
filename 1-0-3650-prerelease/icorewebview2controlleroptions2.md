---
description: This is the interface in ControllerOptions for ScriptLocale.
title: WebView2 Win32 C++ ICoreWebView2ControllerOptions2
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerOptions2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerOptions2
- ICoreWebView2ControllerOptions2.get_ScriptLocale
- ICoreWebView2ControllerOptions2.put_ScriptLocale
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerOptions2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ControllerOptions2
  : public ICoreWebView2ControllerOptions
```

This is the interface in ControllerOptions for ScriptLocale.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ScriptLocale](#get_scriptlocale) | Gets the `ScriptLocale` property.
[put_ScriptLocale](#put_scriptlocale) | The default locale for the WebView2.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_ScriptLocale

Gets the `ScriptLocale` property.

> public HRESULT [get_ScriptLocale](#get_scriptlocale)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_ScriptLocale

The default locale for the WebView2.

> public HRESULT [put_ScriptLocale](#put_scriptlocale)(LPCWSTR value)

It sets the default locale for all Intl JavaScript APIs and other JavaScript APIs that depend on it, namely `Intl.DateTimeFormat()` which affects string formatting like in the time/date formats. Example: `Intl.DateTimeFormat().format(new Date())` The intended locale value is in the format of BCP 47 Language Tags. More information can be found from [IETF BCP47](https://www.ietf.org/rfc/bcp/bcp47.html).

This property sets the locale for a CoreWebView2Environment used to create the WebView2ControllerOptions object, which is passed as a parameter in `CreateCoreWebView2ControllerWithOptions`.

Changes to the ScriptLocale property apply to renderer processes created after the change. Any existing renderer processes will continue to use the previous ScriptLocale value. To ensure changes are applied to all renderer process, close and restart the CoreWebView2Environment and all associated WebView2 objects.

The default value for ScriptLocale will depend on the WebView2 language and OS region. If the language portions of the WebView2 language and OS region match, then it will use the OS region. Otherwise, it will use the WebView2 language.

OS Region   |WebView2 Language   |Default WebView2 ScriptLocale
--------- | --------- | ---------
en-GB   |en-US   |en-GB
es-MX   |en-US   |en-US
en-US   |en-GB   |en-US

You can set the ScriptLocale to the empty string to get the default ScriptLocale value.

Use OS specific APIs to determine the OS region to use with this property if you want to match the OS. For example:

Win32 C++: 
```cpp
wchar_t osLocale[LOCALE_NAME_MAX_LENGTH] = {0};
GetUserDefaultLocaleName(osLocale, LOCALE_NAME_MAX_LENGTH);
```

```cpp
    wil::com_ptr<ICoreWebView2ControllerOptions2> webView2ControllerOptions2;
    if (SUCCEEDED(options->QueryInterface(IID_PPV_ARGS(&webView2ControllerOptions2))))
    {
        if (m_webviewOption.useOSRegion)
        {
            wchar_t osLocale[LOCALE_NAME_MAX_LENGTH] = {0};
            GetUserDefaultLocaleName(osLocale, LOCALE_NAME_MAX_LENGTH);
            CHECK_FAILURE(webView2ControllerOptions2->put_ScriptLocale(osLocale));
        }
        else if (!m_webviewOption.scriptLocale.empty())
        {
            CHECK_FAILURE(webView2ControllerOptions2->put_ScriptLocale(
                m_webviewOption.scriptLocale.c_str()));
        }
    }
```

