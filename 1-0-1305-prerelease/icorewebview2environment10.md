---
description: This interface is used to create ICoreWebView2ControllerOptions object, which can be passed as a parameter in `CreateCoreWebView2ControllerWithOptions` and `CreateCoreWebView2CompositionControllerWithOptions` function for multiple profiles support.
title: WebView2 Win32 C++ ICoreWebView2Environment10
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment10
---

# interface ICoreWebView2Environment10

```
interface ICoreWebView2Environment10
  : public ICoreWebView2Environment9
```

This interface is used to create [ICoreWebView2ControllerOptions](icorewebview2controlleroptions.md) object, which can be passed as a parameter in `CreateCoreWebView2ControllerWithOptions` and `CreateCoreWebView2CompositionControllerWithOptions` function for multiple profiles support.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2CompositionControllerWithOptions](#createcorewebview2compositioncontrollerwithoptions) | Create a new WebView in visual hosting mode with options.
[CreateCoreWebView2ControllerOptions](#createcorewebview2controlleroptions) | Create a new [ICoreWebView2ControllerOptions](icorewebview2controlleroptions.md) to be passed as a parameter of CreateCoreWebView2ControllerWithOptions and CreateCoreWebView2CompositionControllerWithOptions.
[CreateCoreWebView2ControllerWithOptions](#createcorewebview2controllerwithoptions) | Create a new WebView with options.

The profile will be created on disk or opened when calling `CreateCoreWebView2ControllerWithOptions` or `CreateCoreWebView2CompositionControllerWithOptions` no matter InPrivate mode is enabled or not, and it will be released in memory when the corresponding controller is closed but still remain on disk. If you create a WebView2Controller with {ProfileName="name", InPrivate=false} and then later create another one with {ProfileName="name", InPrivate=true}, these two controllers using the same profile would be allowed to run at the same time. As WebView2 is built on top of Edge browser, it follows Edge's behavior pattern. To create an InPrivate WebView, we gets an off-the-record profile (an InPrivate profile) from a regular profile, then create the WebView with the off-the-record profile.

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

#### CreateCoreWebView2CompositionControllerWithOptions

Create a new WebView in visual hosting mode with options.

> public HRESULT [CreateCoreWebView2CompositionControllerWithOptions](#createcorewebview2compositioncontrollerwithoptions)(HWND parentWindow, [ICoreWebView2ControllerOptions](icorewebview2controlleroptions.md) * options, [ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler](icorewebview2createcorewebview2compositioncontrollercompletedhandler.md) * handler)

#### CreateCoreWebView2ControllerOptions

Create a new [ICoreWebView2ControllerOptions](icorewebview2controlleroptions.md) to be passed as a parameter of CreateCoreWebView2ControllerWithOptions and CreateCoreWebView2CompositionControllerWithOptions.

> public HRESULT [CreateCoreWebView2ControllerOptions](#createcorewebview2controlleroptions)([ICoreWebView2ControllerOptions](icorewebview2controlleroptions.md) ** options)

The 'options' is settable and in it the default value for profile name is the empty string, and the default value for IsInPrivateModeEnabled is false. Also the profile name can be reused.

#### CreateCoreWebView2ControllerWithOptions

Create a new WebView with options.

> public HRESULT [CreateCoreWebView2ControllerWithOptions](#createcorewebview2controllerwithoptions)(HWND parentWindow, [ICoreWebView2ControllerOptions](icorewebview2controlleroptions.md) * options, [ICoreWebView2CreateCoreWebView2ControllerCompletedHandler](icorewebview2createcorewebview2controllercompletedhandler.md) * handler)

