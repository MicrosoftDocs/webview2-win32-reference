---
description: This interface is used to manage profile options that created by 'CreateCoreWebView2ControllerOptions'.
title: WebView2 Win32 C++ ICoreWebView2ControllerOptions
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerOptions
---

# interface ICoreWebView2ControllerOptions

```
interface ICoreWebView2ControllerOptions
  : public IUnknown
```

This interface is used to manage profile options that created by 'CreateCoreWebView2ControllerOptions'.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled) | `IsInPrivateModeEnabled` property is to enable/disable InPrivate mode.
[get_ProfileName](#get_profilename) | `ProfileName` property is to specify a profile name, which is only allowed to contain the following ASCII characters.
[put_IsInPrivateModeEnabled](#put_isinprivatemodeenabled) | Sets the `IsInPrivateModeEnabled` property.
[put_ProfileName](#put_profilename) | Sets the `ProfileName` property.

```cpp
    auto webViewEnvironment10 = m_webViewEnvironment.try_query<ICoreWebView2Environment10>();
    if (!webViewEnvironment10)
    {
        FeatureNotAvailable();
        return S_OK;
    }

    wil::com_ptr<ICoreWebView2ControllerOptions> options;
    // The validation of parameters occurs when setting the properties.
    HRESULT hr = webViewEnvironment10->CreateCoreWebView2ControllerOptions(&options);
    if (hr == E_INVALIDARG)
    {
        ShowFailure(hr, L"Unable to create WebView2 due to an invalid profile name.");
        CloseAppWindow();
        return S_OK;
    }
    CHECK_FAILURE(hr);
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1210.39
WebView2 Win32 Prerelease |    1.0.1222

## Members

#### get_IsInPrivateModeEnabled

`IsInPrivateModeEnabled` property is to enable/disable InPrivate mode.

> public HRESULT [get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled)(BOOL * value)

#### get_ProfileName

`ProfileName` property is to specify a profile name, which is only allowed to contain the following ASCII characters.

> public HRESULT [get_ProfileName](#get_profilename)(LPWSTR * value)

It has a maximum length of 64 characters excluding the null-terminator. It is ASCII case insensitive.

* alphabet characters: a-z and A-Z

* digit characters: 0-9

* and '#', '@', '$', '(', ')', '+', '-', '_', '~', '.', ' ' (space).

Note: the text must not end with a period '.' or ' ' (space). And, although upper-case letters are allowed, they're treated just as lower-case counterparts because the profile name will be mapped to the real profile directory path on disk and Windows file system handles path names in a case-insensitive way.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_IsInPrivateModeEnabled

Sets the `IsInPrivateModeEnabled` property.

> public HRESULT [put_IsInPrivateModeEnabled](#put_isinprivatemodeenabled)(BOOL value)

#### put_ProfileName

Sets the `ProfileName` property.

> public HRESULT [put_ProfileName](#put_profilename)(LPCWSTR value)

