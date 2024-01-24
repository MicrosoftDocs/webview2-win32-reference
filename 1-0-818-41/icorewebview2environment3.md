---
description: A continuation of the ICoreWebView2Environment2 interface.
title: WebView2 Win32 C++ ICoreWebView2Environment3
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 06/01/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment3
---

# interface ICoreWebView2Environment3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Environment3
  : public ICoreWebView2Environment2
```

A continuation of the [ICoreWebView2Environment2](icorewebview2environment2.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2CompositionController](#createcorewebview2compositioncontroller) | Asynchronously create a new WebView for use with visual hosting.
[CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo) | Create an empty [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### CreateCoreWebView2CompositionController

Asynchronously create a new WebView for use with visual hosting.

> public HRESULT [CreateCoreWebView2CompositionController](#createcorewebview2compositioncontroller)(HWND parentWindow, [ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler](icorewebview2createcorewebview2compositioncontrollercompletedhandler.md) * handler)

parentWindow is the HWND in which the app will connect the visual tree of the WebView. This will be the HWND that the app will receive pointer/ mouse input meant for the WebView (and will need to use SendMouseInput/ SendPointerInput to forward). If the app moves the WebView visual tree to underneath a different window, then it needs to call put_ParentWindow to update the new parent HWND of the visual tree.

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
    auto options = Microsoft::WRL::Make<CoreWebView2EnvironmentOptions>();
    CHECK_FAILURE(options->put_AllowSingleSignOnUsingOSPrimaryAccount(
        m_AADSSOEnabled ? TRUE : FALSE));
    if (!m_language.empty())
        CHECK_FAILURE(options->put_Language(m_language.c_str()));
    HRESULT hr = CreateCoreWebView2EnvironmentWithOptions(
        subFolder, nullptr, options.Get(),
        Callback<ICoreWebView2CreateCoreWebView2EnvironmentCompletedHandler>(
            this, &AppWindow::OnCreateEnvironmentCompleted)
            .Get());
    if (!SUCCEEDED(hr))
    {
        if (hr == HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND))
        {
            MessageBox(
                m_mainWindow,
                L"Couldn't find Edge installation. "
                "Do you have a version installed that's compatible with this "
                "WebView2 SDK version?",
                nullptr, MB_OK);
        }
        else
        {
            ShowFailure(hr, L"Failed to create webview environment");
        }
    }
}
// This is the callback passed to CreateWebViewEnvironmentWithOptions.
// Here we simply create the WebView.
HRESULT AppWindow::OnCreateEnvironmentCompleted(
    HRESULT result, ICoreWebView2Environment* environment)
{
    CHECK_FAILURE(result);
    m_webViewEnvironment = environment;

    auto webViewEnvironment3 =
        m_webViewEnvironment.try_query<ICoreWebView2Environment3>();
    if (webViewEnvironment3 && (m_dcompDevice || m_wincompCompositor))
    {
        CHECK_FAILURE(webViewEnvironment3->CreateCoreWebView2CompositionController(
            m_mainWindow,
            Callback<
                ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler>(
                [this](
                    HRESULT result,
                    ICoreWebView2CompositionController* compositionController) -> HRESULT {
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

#### CreateCoreWebView2PointerInfo

Create an empty [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md).

> public HRESULT [CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo)([ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) ** pointerInfo)

The returned [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) needs to be populated with all of the relevant info before calling SendPointerInput.

