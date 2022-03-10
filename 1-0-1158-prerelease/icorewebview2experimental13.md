---
description: This is the ICoreWebView2 Experimental Status Bar interface.
title: WebView2 Win32 C++ ICoreWebView2Experimental13
ms.date: 03/10/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental13
---

# interface ICoreWebView2Experimental13

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental13
  : public IUnknown
```

This is the ICoreWebView2 Experimental Status Bar interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_StatusBarTextChanged](#add_statusbartextchanged) | Add an event handler for the `StatusBarTextChanged` event.
[get_StatusBarText](#get_statusbartext) | 
[remove_StatusBarTextChanged](#remove_statusbartextchanged) | Remove an event handler previously added with `add_StatusBarTextChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### add_StatusBarTextChanged

Add an event handler for the `StatusBarTextChanged` event.

> public HRESULT [add_StatusBarTextChanged](#add_statusbartextchanged)([ICoreWebView2ExperimentalStatusBarTextChangedEventHandler](icorewebview2experimentalstatusbartextchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`StatusBarTextChanged` fires when the WebView is showing a status message, a URL, or an empty string (an indication to hide the status bar). 
```cpp
    m_statusBar.Initialize(appWindow);
    // Registering a listener for status bar message changes
    CHECK_FAILURE(m_webViewExperimental13->add_StatusBarTextChanged(
        Microsoft::WRL::Callback<ICoreWebView2ExperimentalStatusBarTextChangedEventHandler>(
            [this](ICoreWebView2* sender, IUnknown* args) -> HRESULT {
                if (m_customStatusBar)
                {
                    wil::unique_cotaskmem_string value;
                    Microsoft::WRL::ComPtr<ICoreWebView2Experimental13> wv;
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

#### get_StatusBarText

> public HRESULT [get_StatusBarText](#get_statusbartext)(LPWSTR * value)

#### remove_StatusBarTextChanged

Remove an event handler previously added with `add_StatusBarTextChanged`.

> public HRESULT [remove_StatusBarTextChanged](#remove_statusbartextchanged)(EventRegistrationToken token)

