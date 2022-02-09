---
description: This is a continuation of the `ICoreWebView2Profile` interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile2
ms.date: 02/08/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile2
---

# interface ICoreWebView2ExperimentalProfile2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile2
  : public IUnknown
```

This is a continuation of the `ICoreWebView2Profile` interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_PreferredColorScheme](#get_preferredcolorscheme) | The PreferredColorScheme property sets the overall color scheme of the WebView2s associated with this profile.
[put_PreferredColorScheme](#put_preferredcolorscheme) | Sets the `PreferredColorScheme` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_PreferredColorScheme

The PreferredColorScheme property sets the overall color scheme of the WebView2s associated with this profile.

> public HRESULT [get_PreferredColorScheme](#get_preferredcolorscheme)(COREWEBVIEW2_PREFERRED_COLOR_SCHEME * value)

This sets the color scheme for WebView2 UI like dialogs, prompts, and context menus by setting the media feature `prefers-color-scheme` for websites to respond to.

The default value for this is COREWEBVIEW2_PREFERRED_COLOR_AUTO, which will follow whatever theme the OS is currently set to.

```cpp
void ViewComponent::SetPreferredColorScheme(COREWEBVIEW2_PREFERRED_COLOR_SCHEME value)
{
    wil::com_ptr<ICoreWebView2Experimental8> webViewExperimental8;
    webViewExperimental8 = m_webView.try_query<ICoreWebView2Experimental8>();

    if (webViewExperimental8)
    {
      wil::com_ptr<ICoreWebView2ExperimentalProfile> profile;
      CHECK_FAILURE(webViewExperimental8->get_Profile(&profile));

      auto profileExperimental2 =
        profile.try_query<ICoreWebView2ExperimentalProfile2>();
      if (profileExperimental2)
      {
        profileExperimental2->put_PreferredColorScheme(value);
      }
    }
}
```
 Returns the value of the `PreferredColorScheme` property.

#### put_PreferredColorScheme

Sets the `PreferredColorScheme` property.

> public HRESULT [put_PreferredColorScheme](#put_preferredcolorscheme)(COREWEBVIEW2_PREFERRED_COLOR_SCHEME value)

