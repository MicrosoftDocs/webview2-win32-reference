---
description: Provides a set of properties to configure a Profile object.
title: WebView2 Win32 C++ ICoreWebView2Profile
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile
---

# interface ICoreWebView2Profile

```
interface ICoreWebView2Profile
  : public IUnknown
```

Provides a set of properties to configure a Profile object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultDownloadFolderPath](#get_defaultdownloadfolderpath) | Gets the `DefaultDownloadFolderPath` property.
[get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled) | InPrivate mode is enabled or not.
[get_PreferredColorScheme](#get_preferredcolorscheme) | The PreferredColorScheme property sets the overall color scheme of the WebView2s associated with this profile.
[get_ProfileName](#get_profilename) | Name of the profile.
[get_ProfilePath](#get_profilepath) | Full path of the profile directory.
[put_DefaultDownloadFolderPath](#put_defaultdownloadfolderpath) | Sets the `DefaultDownloadFolderPath` property.
[put_PreferredColorScheme](#put_preferredcolorscheme) | Sets the `PreferredColorScheme` property.

```cpp
        CHECK_FAILURE(webViewEnvironment10->CreateCoreWebView2CompositionControllerWithOptions(
            m_mainWindow, options.get(),
            Callback<ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler>(
                [this](
                    HRESULT result,
                    ICoreWebView2CompositionController* compositionController) -> HRESULT {
                    auto controller =
                        wil::com_ptr<ICoreWebView2CompositionController>(compositionController)
                            .query<ICoreWebView2Controller>();
                    return OnCreateCoreWebView2ControllerCompleted(result, controller.get());
                })
                .Get()));
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1210.39
WebView2 Win32 Prerelease |    1.0.1222

## Members

#### get_DefaultDownloadFolderPath

Gets the `DefaultDownloadFolderPath` property.

> public HRESULT [get_DefaultDownloadFolderPath](#get_defaultdownloadfolderpath)(LPWSTR * value)

The default value is the system default download folder path for the user.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_IsInPrivateModeEnabled

InPrivate mode is enabled or not.

> public HRESULT [get_IsInPrivateModeEnabled](#get_isinprivatemodeenabled)(BOOL * value)

#### get_PreferredColorScheme

The PreferredColorScheme property sets the overall color scheme of the WebView2s associated with this profile.

> public HRESULT [get_PreferredColorScheme](#get_preferredcolorscheme)(COREWEBVIEW2_PREFERRED_COLOR_SCHEME * value)

This sets the color scheme for WebView2 UI like dialogs, prompts, and context menus by setting the media feature `prefers-color-scheme` for websites to respond to.

The default value for this is COREWEBVIEW2_PREFERRED_COLOR_AUTO, which will follow whatever theme the OS is currently set to.

```cpp
void ViewComponent::SetPreferredColorScheme(COREWEBVIEW2_PREFERRED_COLOR_SCHEME value)
{
    wil::com_ptr<ICoreWebView2_13> webView2_13;
    webView2_13 = m_webView.try_query<ICoreWebView2_13>();

    if (webView2_13)
    {
        wil::com_ptr<ICoreWebView2Profile> profile;
        CHECK_FAILURE(webView2_13->get_Profile(&profile));
        profile->put_PreferredColorScheme(value);
    }
}
```
 Returns the value of the `PreferredColorScheme` property.

#### get_ProfileName

Name of the profile.

> public HRESULT [get_ProfileName](#get_profilename)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ProfilePath

Full path of the profile directory.

> public HRESULT [get_ProfilePath](#get_profilepath)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_DefaultDownloadFolderPath

Sets the `DefaultDownloadFolderPath` property.

> public HRESULT [put_DefaultDownloadFolderPath](#put_defaultdownloadfolderpath)(LPCWSTR value)

The default download folder path is persisted in the user data folder across sessions. The value should be an absolute path to a folder that the user and application can write to. Returns `E_INVALIDARG` if the value is invalid, and the default download folder path is not changed. Otherwise the path is changed immediately. If the directory does not yet exist, it is created at the time of the next download. If the host application does not have permission to create the directory, then the user is prompted to provide a new path through the Save As dialog. The user can override the default download folder path for a given download by choosing a different path in the Save As dialog.

#### put_PreferredColorScheme

Sets the `PreferredColorScheme` property.

> public HRESULT [put_PreferredColorScheme](#put_preferredcolorscheme)(COREWEBVIEW2_PREFERRED_COLOR_SCHEME value)

