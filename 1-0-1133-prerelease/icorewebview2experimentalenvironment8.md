---
description: This interface is used to create CreateCoreWebView2ControllerOptions object, which can be passed as a parameter in 'CreateCoreWebView2ControllerWithOptions' and 'CreateCoreWebView2CompositionControllerWithOptions' function for multiple profile support.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment8
ms.date: 02/09/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment8
---

# interface ICoreWebView2ExperimentalEnvironment8

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment8
  : public IUnknown
```

This interface is used to create CreateCoreWebView2ControllerOptions object, which can be passed as a parameter in 'CreateCoreWebView2ControllerWithOptions' and 'CreateCoreWebView2CompositionControllerWithOptions' function for multiple profile support.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2CompositionControllerWithOptions](#createcorewebview2compositioncontrollerwithoptions) | Create a new WebView in visual hosting mode with options.
[CreateCoreWebView2ControllerOptions](#createcorewebview2controlleroptions) | Create a new [ICoreWebView2ExperimentalControllerOptions](icorewebview2experimentalcontrolleroptions.md) to be passed as a parameter of CreateCoreWebView2ControllerWithOptions and CreateCoreWebView2CompositionControllerWithOptions.
[CreateCoreWebView2ControllerWithOptions](#createcorewebview2controllerwithoptions) | Create a new WebView with options.

```cpp
    auto webViewEnvironment8 =
        m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment8>();
    if (!webViewEnvironment8)
    {
        FeatureNotAvailable();
        return S_OK;
    }

    Microsoft::WRL::ComPtr<ICoreWebView2ExperimentalControllerOptions> options;
    HRESULT hr = webViewEnvironment8->CreateCoreWebView2ControllerOptions(
        m_webviewOption.profile.c_str(), m_webviewOption.isInPrivate, options.GetAddressOf());
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### CreateCoreWebView2CompositionControllerWithOptions

Create a new WebView in visual hosting mode with options.

> public HRESULT [CreateCoreWebView2CompositionControllerWithOptions](#createcorewebview2compositioncontrollerwithoptions)(HWND parentWindow, [ICoreWebView2ExperimentalControllerOptions](icorewebview2experimentalcontrolleroptions.md) * options, [ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler](icorewebview2createcorewebview2compositioncontrollercompletedhandler.md) * handler)

#### CreateCoreWebView2ControllerOptions

Create a new [ICoreWebView2ExperimentalControllerOptions](icorewebview2experimentalcontrolleroptions.md) to be passed as a parameter of CreateCoreWebView2ControllerWithOptions and CreateCoreWebView2CompositionControllerWithOptions.

> public HRESULT [CreateCoreWebView2ControllerOptions](#createcorewebview2controlleroptions)(LPCWSTR profileName, BOOL isInPrivateModeEnabled, [ICoreWebView2ExperimentalControllerOptions](icorewebview2experimentalcontrolleroptions.md) ** options)

#### CreateCoreWebView2ControllerWithOptions

Create a new WebView with options.

> public HRESULT [CreateCoreWebView2ControllerWithOptions](#createcorewebview2controllerwithoptions)(HWND parentWindow, [ICoreWebView2ExperimentalControllerOptions](icorewebview2experimentalcontrolleroptions.md) * options, [ICoreWebView2CreateCoreWebView2ControllerCompletedHandler](icorewebview2createcorewebview2controllercompletedhandler.md) * handler)

