---
description: This interface is an extension of ICoreWebView2_11 that supports status bar events.
title: WebView2 Win32 C++ ICoreWebView2_12
ms.date: 04/12/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_12
---

# interface ICoreWebView2_12

```
interface ICoreWebView2_12
  : public ICoreWebView2_11
```

This interface is an extension of ICoreWebView2_11 that supports status bar events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_StatusBarTextChanged](#add_statusbartextchanged) | Add an event handler for the `StatusBarTextChanged` event.
[get_Profile](#get_profile) | The associated [ICoreWebView2Profile](icorewebview2profile.md) object.
[get_StatusBarText](#get_statusbartext) | The status message text.
[remove_StatusBarTextChanged](#remove_statusbartextchanged) | Remove an event handler previously added with `add_StatusBarTextChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### add_StatusBarTextChanged

Add an event handler for the `StatusBarTextChanged` event.

> public HRESULT [add_StatusBarTextChanged](#add_statusbartextchanged)([ICoreWebView2StatusBarTextChangedEventHandler](icorewebview2statusbartextchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`StatusBarTextChanged` fires when the WebView is showing a status message, a URL, or an empty string (an indication to hide the status bar). 
```cpp
        m_statusBar.Initialize(appWindow);
        // Registering a listener for status bar message changes
        CHECK_FAILURE(m_webView2_12->add_StatusBarTextChanged(
            Microsoft::WRL::Callback<ICoreWebView2StatusBarTextChangedEventHandler>(
                [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                    if (m_customStatusBar)
                    {
                        wil::unique_cotaskmem_string value;
                        Microsoft::WRL::ComPtr<ICoreWebView2_12> wv;
                        CHECK_FAILURE(sender->QueryInterface(IID_PPV_ARGS(&wv)));

                        CHECK_FAILURE(wv->get_StatusBarText(&value));
                        std::wstring valueString = value.get();
                        if (valueString.length() != 0)
                        {
                            m_statusBar.Show(valueString);
                        }
                        else
                        {
                            m_statusBar.Hide();
                        }
                    }

                    return S_OK;
                })
                .Get(),
            &m_statusBarTextChangedToken));
```

#### get_Profile

The associated [ICoreWebView2Profile](icorewebview2profile.md) object.

> public HRESULT [get_Profile](#get_profile)([ICoreWebView2Profile](icorewebview2profile.md) ** value)

If this CoreWebView2 was created with a CoreWebView2ControllerOptions, the CoreWebView2Profile will match those specified options. Otherwise if this CoreWebView2 was created without a CoreWebView2ControllerOptions, then this will be the default CoreWebView2Profile for the corresponding CoreWebView2Environment.

#### get_StatusBarText

The status message text.

> public HRESULT [get_StatusBarText](#get_statusbartext)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### remove_StatusBarTextChanged

Remove an event handler previously added with `add_StatusBarTextChanged`.

> public HRESULT [remove_StatusBarTextChanged](#remove_statusbartextchanged)(EventRegistrationToken token)

