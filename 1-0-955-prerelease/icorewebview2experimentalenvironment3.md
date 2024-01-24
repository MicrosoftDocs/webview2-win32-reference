---
description: This interface is an extension of the ICoreWebView2Environment that manages updating Edge WebView2 Runtime.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment3
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/14/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment3
---

# interface ICoreWebView2ExperimentalEnvironment3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment3
  : public IUnknown
```

This interface is an extension of the [ICoreWebView2Environment](icorewebview2environment.md) that manages updating Edge WebView2 Runtime.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[UpdateRuntime](#updateruntime) | Try to update the installed Microsoft Edge WebView2 Runtime.
[COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind) | Specifies the browser process exit type used in the [ICoreWebView2ExperimentalBrowserProcessExitedEventArgs](icorewebview2experimentalbrowserprocessexitedeventargs.md) interface.
[COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) | Matrix that represents a 3D transform.
[COREWEBVIEW2_PDF_TOOLBAR_ITEMS](#corewebview2_pdf_toolbar_items) | Specifies the PDF toolbar item types used for the `ICoreWebView2StagingSettings::put_HiddenPdfToolbarItems` method.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.

An object implementing the ICoreWebView2ExperimentalEnvironment3 interface will also implement [ICoreWebView2Environment](icorewebview2environment.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.865

## Members

#### UpdateRuntime

Try to update the installed Microsoft Edge WebView2 Runtime.

> public HRESULT [UpdateRuntime](#updateruntime)([ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler](icorewebview2experimentalupdateruntimecompletedhandler.md) * handler)

This will potentially result in a new version of the Edge WebView2 Runtime being installed and `NewBrowserVersionAvailable` event being raised. There is no guarantee on the order of that event being raised and UpdateRuntime's completed handler being invoked. Besides the `NewBrowserVersionAvailable` event, there will be no impact to any currently running WebView2s when the update is installed. Even though the Edge WebView2 Runtime update is installed for the machine and available to all users, the update will happen silently and not show elevation prompt. This will not impact Edge browser installations. The latest version can always be queried using the `GetAvailableCoreWebView2BrowserVersionString` API. The UpdateRuntime method is only supported for an installed Edge WebView2 Runtime. When running a fixed version Edge WebView2 Runtime or non stable channel Edge browser, this API will return `HRESULT_FROM_WIN32(ERROR_NOT_SUPPORTED)`. There could only be one active UpdateRuntime operation in an app process, and calling this API before the completed handler for a previous call is invoked will fail with `HRESULT_FROM_WIN32(ERROR_BUSY)`. Calling this API repeatedly in a short period of time, will also fail with `HRESULT_FROM_WIN32(ERROR_BUSY)`. To protect accidental abuse of the update service, the implementation throttles the calls of this API to 3 times within 5 minutes in a process. The exact throttling limit can change in the future. Edge update service can only support one update request at a time globally. If there is already an update operation running in the Edge update service, UpdateRuntime request will result in the completed handler being invoked with a result that has `Status` of `COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING`. As the running update could succeed or fail, the app should retry later if `NewBrowserVersionAvailable` event has not been raised. The UpdateRuntime operation is associated with the CoreWebView2Environment object and any ongoing UpdateRuntime operation will be aborted when the associated CoreWebView2Environment along with the CoreWebView2 objects that are created by the CoreWebView2Environment object are all released. In this case, the completed handler will be invoked with `S_OK` as `errorCode` and a result object with `Status` of COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED and `ExtendedError` as `E_ABORT`.

```cpp
        auto experimentalEnvironment3 =
            m_webViewEnvironment.try_query<ICoreWebView2ExperimentalEnvironment3>();
        CHECK_FEATURE_RETURN(experimentalEnvironment3);
        HRESULT hr = experimentalEnvironment3->UpdateRuntime(
            Callback<ICoreWebView2ExperimentalUpdateRuntimeCompletedHandler>(
                [](HRESULT errorCode,
                   ICoreWebView2ExperimentalUpdateRuntimeResult* result) -> HRESULT {
                    HRESULT updateError = E_FAIL;
                    COREWEBVIEW2_UPDATE_RUNTIME_STATUS status =
                        COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED;
                    if ((errorCode == S_OK) && result)
                    {
                        CHECK_FAILURE(result->get_Status(&status));
                        CHECK_FAILURE(result->get_ExtendedError(&updateError));
                    }
                    std::wstringstream formattedMessage;
                    formattedMessage << "UpdateRuntime result (0x" << std::hex << errorCode
                                     << "), status(" << status << "), extendedError("
                                     << updateError << ")";
                    MessageBox(nullptr, formattedMessage.str().c_str(), nullptr, MB_OK);
                    return S_OK;
                })
                .Get());
        if (FAILED(hr))
            ShowFailure(hr, L"Call to TryUpdateRuntime failed");
```

#### COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND

Specifies the browser process exit type used in the [ICoreWebView2ExperimentalBrowserProcessExitedEventArgs](icorewebview2experimentalbrowserprocessexitedeventargs.md) interface.

> enum [COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_NORMAL            | Indicates that the browser process ended normally.
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_FAILED            | Indicates that the browser process ended unexpectedly.

#### COREWEBVIEW2_MATRIX_4X4

Matrix that represents a 3D transform.

> typedef [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4)

This transform is used to calculate correct coordinates when calling CreateCoreWebView2PointerInfoFromPointerId. This is equivalent to a D2D1_MATRIX_4X4_F

#### COREWEBVIEW2_PDF_TOOLBAR_ITEMS

Specifies the PDF toolbar item types used for the `ICoreWebView2StagingSettings::put_HiddenPdfToolbarItems` method.

> enum [COREWEBVIEW2_PDF_TOOLBAR_ITEMS](#corewebview2_pdf_toolbar_items)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE            | No item.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE            | The save button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PRINT            | The print button.
COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE_AS            | The save as button.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

Status of UpdateRuntime operation result.

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

