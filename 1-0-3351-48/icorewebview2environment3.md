---
description: A continuation of the ICoreWebView2Environment2 interface.
title: WebView2 Win32 C++ ICoreWebView2Environment3
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment3
- ICoreWebView2Environment3.CreateCoreWebView2CompositionController
- ICoreWebView2Environment3.CreateCoreWebView2PointerInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment3

```
interface ICoreWebView2Environment3
  : public ICoreWebView2Environment2
```

A continuation of the [ICoreWebView2Environment2](icorewebview2environment2.md#icorewebview2environment2) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2CompositionController](#createcorewebview2compositioncontroller) | Asynchronously create a new WebView for use with visual hosting.
[CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo) | Create an empty [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md#icorewebview2pointerinfo).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### CreateCoreWebView2CompositionController

Asynchronously create a new WebView for use with visual hosting.

> public HRESULT [CreateCoreWebView2CompositionController](#createcorewebview2compositioncontroller)(HWND ParentWindow, [ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler](icorewebview2createcorewebview2compositioncontrollercompletedhandler.md#icorewebview2createcorewebview2compositioncontrollercompletedhandler) * handler)

parentWindow is the HWND in which the app will connect the visual tree of the WebView. This will be the HWND that the app will receive pointer/ mouse input meant for the WebView (and will need to use SendMouseInput/ SendPointerInput to forward). If the app moves the WebView visual tree to underneath a different window, then it needs to call put_ParentWindow to update the new parent HWND of the visual tree.

HWND_MESSAGE is not a valid parameter for `parentWindow` for visual hosting. The underlying implementation of supporting HWND_MESSAGE would break accessibility for visual hosting. This is supported in windowed WebViews - see CreateCoreWebView2Controller.

Use put_RootVisualTarget on the created CoreWebView2CompositionController to provide a visual to host the browser's visual tree.

It is recommended that the application set Application User Model ID for the process or the application window. If none is set, during WebView creation a generated Application User Model ID is set to root window of parentWindow. 
```cpp
// Create or recreate the WebView and its environment.
void AppWindow::InitializeWebView()
{
    // To ensure browser switches get applied correctly, we need to close
    // the existing WebView. This will result in a new browser process
    // getting created which will apply the browser switches.
    CloseWebView();
    m_dcompDevice = nullptr;
    m_wincompCompositor = nullptr;
    LPCWSTR subFolder = nullptr;

    if (m_creationModeId == IDM_CREATION_MODE_VISUAL_DCOMP ||
        m_creationModeId == IDM_CREATION_MODE_TARGET_DCOMP)
    {
        HRESULT hr = DCompositionCreateDevice2(nullptr, IID_PPV_ARGS(&m_dcompDevice));
        if (!SUCCEEDED(hr))
        {
            MessageBox(
                m_mainWindow,
                L"Attempting to create WebView using DComp Visual is not supported.\r\n"
                "DComp device creation failed.\r\n"
                "Current OS may not support DComp.",
                L"Create with Windowless DComp Visual Failed", MB_OK);
            return;
        }
    }
    else if (m_creationModeId == IDM_CREATION_MODE_VISUAL_WINCOMP)
    {
        HRESULT hr = TryCreateDispatcherQueue();
        if (!SUCCEEDED(hr))
        {
            MessageBox(
                m_mainWindow,
                L"Attempting to create WebView using WinComp Visual is not supported.\r\n"
                "WinComp compositor creation failed.\r\n"
                "Current OS may not support WinComp.",
                L"Create with Windowless WinComp Visual Failed", MB_OK);
            return;
        }
        m_wincompCompositor = winrtComp::Compositor();
    }

    std::wstring args;
    args.append(L"--enable-features=ThirdPartyStoragePartitioning,PartitionedCookies");
    auto options = Microsoft::WRL::Make<CoreWebView2EnvironmentOptions>();
    options->put_AdditionalBrowserArguments(args.c_str());
    CHECK_FAILURE(
        options->put_AllowSingleSignOnUsingOSPrimaryAccount(m_AADSSOEnabled ? TRUE : FALSE));
    CHECK_FAILURE(options->put_ExclusiveUserDataFolderAccess(
        m_ExclusiveUserDataFolderAccess ? TRUE : FALSE));
    if (!m_language.empty())
        CHECK_FAILURE(options->put_Language(m_language.c_str()));
    CHECK_FAILURE(options->put_IsCustomCrashReportingEnabled(
        m_CustomCrashReportingEnabled ? TRUE : FALSE));

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions4> options4;
    if (options.As(&options4) == S_OK)
    {
        const WCHAR* allowedOrigins[1] = {L"https://*.example.com"};

        auto customSchemeRegistration =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"custom-scheme");
        customSchemeRegistration->SetAllowedOrigins(1, allowedOrigins);
        auto customSchemeRegistration2 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"wv2rocks");
        customSchemeRegistration2->put_TreatAsSecure(TRUE);
        customSchemeRegistration2->SetAllowedOrigins(1, allowedOrigins);
        customSchemeRegistration2->put_HasAuthorityComponent(TRUE);
        auto customSchemeRegistration3 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(
                L"custom-scheme-not-in-allowed-origins");
        ICoreWebView2CustomSchemeRegistration* registrations[3] = {
            customSchemeRegistration.Get(), customSchemeRegistration2.Get(),
            customSchemeRegistration3.Get()};
        options4->SetCustomSchemeRegistrations(
            2, static_cast<ICoreWebView2CustomSchemeRegistration**>(registrations));
    }

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions5> options5;
    if (options.As(&options5) == S_OK)
    {
        CHECK_FAILURE(
            options5->put_EnableTrackingPrevention(m_TrackingPreventionEnabled ? TRUE : FALSE));
    }

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions6> options6;
    if (options.As(&options6) == S_OK)
    {
        CHECK_FAILURE(options6->put_AreBrowserExtensionsEnabled(TRUE));
    }

    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions8> options8;
    if (options.As(&options8) == S_OK)
    {
        COREWEBVIEW2_SCROLLBAR_STYLE style = COREWEBVIEW2_SCROLLBAR_STYLE_FLUENT_OVERLAY;
        CHECK_FAILURE(options8->put_ScrollBarStyle(style));
    }

    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, m_userDataFolder.c_str(), options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
    if (!SUCCEEDED(hr))
    {
        switch (hr)
        {
        case HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND):
        {
            MessageBox(
                m_mainWindow,
                L"Couldn't find Edge WebView2 Runtime. "
                "Do you have a version installed?",
                nullptr, MB_OK);
        }
        break;
        case HRESULT_FROM_WIN32(ERROR_FILE_EXISTS):
        {
            MessageBox(
                m_mainWindow,
                L"User data folder cannot be created because a file with the same name already "
                L"exists.",
                nullptr, MB_OK);
        }
        break;
        case E_ACCESSDENIED:
        {
            MessageBox(
                m_mainWindow, L"Unable to create user data folder, Access Denied.", nullptr,
                MB_OK);
        }
        break;
        case E_FAIL:
        {
            MessageBox(m_mainWindow, L"Edge runtime unable to start", nullptr, MB_OK);
        }
        break;
        default:
        {
            ShowFailure(hr, L"Failed to create WebView2 environment");
        }
        }
    }
}
// This is the callback passed to CreateWebViewEnvironmentWithOptions.
// Here we simply create the WebView.
HRESULT AppWindow::OnCreateEnvironmentCompleted(
    HRESULT result, ICoreWebView2Environment* environment)
{
    if (result != S_OK)
    {
        ShowFailure(result, L"Failed to create environment object.");
        return S_OK;
    }
    m_webViewEnvironment = environment;

    if (m_webviewOption.entry == WebViewCreateEntry::EVER_FROM_CREATE_WITH_OPTION_MENU ||
        m_creationModeId == IDM_CREATION_MODE_HOST_INPUT_PROCESSING
    )
    {
        return CreateControllerWithOptions();
    }
    auto webViewEnvironment3 = m_webViewEnvironment.try_query<ICoreWebView2Environment3>();

    if (webViewEnvironment3 && (m_dcompDevice || m_wincompCompositor))
    {
        CHECK_FAILURE(webViewEnvironment3->CreateCoreWebView2CompositionController(
            m_mainWindow,
            Callback<ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler>(
                [this](
                    HRESULT result,
                    ICoreWebView2CompositionController* compositionController) -> HRESULT
                {
                    auto controller =
                        wil::com_ptr<ICoreWebView2CompositionController>(compositionController)
                            .query<ICoreWebView2Controller>();
                    return OnCreateCoreWebView2ControllerCompleted(result, controller.get());
                })
                .Get()));
    }
    else
    {
        CHECK_FAILURE(m_webViewEnvironment->CreateCoreWebView2Controller(
            m_mainWindow, Callback<ICoreWebView2CreateCoreWebView2ControllerCompletedHandler>(
                              this, &AppWindow::OnCreateCoreWebView2ControllerCompleted)
                              .Get()));
    }

    return S_OK;
}
```

It is recommended that the application handles restart manager messages so that it can be restarted gracefully in the case when the app is using Edge for WebView from a certain installation and that installation is being uninstalled. For example, if a user installs Edge from Dev channel and opts to use Edge from that channel for testing the app, and then uninstalls Edge from that channel without closing the app, the app will be restarted to allow uninstallation of the dev channel to succeed. 
```cpp
    case WM_QUERYENDSESSION:
    {
        // yes, we can shut down
        // Register how we might be restarted
        RegisterApplicationRestart(L"--restore", RESTART_NO_CRASH | RESTART_NO_HANG);
        *result = TRUE;
        return true;
    }
    break;
    case WM_ENDSESSION:
    {
        if (wParam == TRUE)
        {
            // save app state and exit.
            PostQuitMessage(0);
            return true;
        }
    }
    break;
```

The app should retry `CreateCoreWebView2CompositionController` upon failure, unless the error code is `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`. When the app retries `CreateCoreWebView2CompositionController` upon failure, it is recommended that the app restarts from creating a new WebView2 Environment. If a WebView2 Runtime update happens, the version associated with a WebView2 Environment may have been removed and causing the object to no longer work. Creating a new WebView2 Environment works since it uses the latest version.

WebView creation fails with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)` if a running instance using the same user data folder exists, and the Environment objects have different `EnvironmentOptions`. For example, if a WebView was created with one language, an attempt to create a WebView with a different language using the same user data folder will fail.

The creation will fail with `E_ABORT` if `parentWindow` is destroyed before the creation is finished. If this is caused by a call to `DestroyWindow`, the creation completed handler will be invoked before `DestroyWindow` returns, so you can use this to cancel creation and clean up resources synchronously when quitting a thread.

In rare cases the creation can fail with `E_UNEXPECTED` if runtime does not have permissions to the user data folder.

CreateCoreWebView2CompositionController is supported in the following versions of Windows:

* Windows 11

* Windows 10

* Windows Server 2019

* Windows Server 2016

#### CreateCoreWebView2PointerInfo

Create an empty [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md#icorewebview2pointerinfo).

> public HRESULT [CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo)([ICoreWebView2PointerInfo](icorewebview2pointerinfo.md#icorewebview2pointerinfo) ** value)

The returned [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md#icorewebview2pointerinfo) needs to be populated with all of the relevant info before calling SendPointerInput.

