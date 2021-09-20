---
description: This interface is an extension of the ICoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2Experimental7
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/20/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental7
---

# interface ICoreWebView2Experimental7

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental7
  : public IUnknown
```

This interface is an extension of the [ICoreWebView2](icorewebview2.md).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PrintToPdf](#printtopdf) | Print the current page to PDF asynchronously with the provided settings.

An object implementing the ICoreWebView2Experimental7 interface will also implement [ICoreWebView2](icorewebview2.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### PrintToPdf

Print the current page to PDF asynchronously with the provided settings.

> public HRESULT [PrintToPdf](#printtopdf)(LPCWSTR resultFilePath, [ICoreWebView2ExperimentalPrintSettings](icorewebview2experimentalprintsettings.md) * printSettings, [ICoreWebView2ExperimentalPrintToPdfCompletedHandler](icorewebview2experimentalprinttopdfcompletedhandler.md) * handler)

See [ICoreWebView2ExperimentalPrintSettings](icorewebview2experimentalprintsettings.md) for description of settings. Passing nullptr for `printSettings` results in default print settings used.

Use `resultFilePath` to specify the path to the PDF file. The host should provide an absolute path, including file name. If the path points to an existing file, the file will be overwritten. If the path is not valid, the method fails with `E_INVALIDARG`.

The async `PrintToPdf` operation completes when the data has been written to the PDF file. At this time the [ICoreWebView2ExperimentalPrintToPdfCompletedHandler](icorewebview2experimentalprinttopdfcompletedhandler.md) is invoked. If the application exits before printing is complete, the file is not saved. Only one `PrintToPdf` operation can be in progress at a time. If `PrintToPdf` is called while a print to PDF job is in progress, the completed handler is immediately invoked with `isSuccessful` set to FALSE.

```cpp
// Shows the user a file selection dialog, then uses the selected path when
// printing to PDF. If `enableLandscape` is true, the page is printed
// in landscape mode, otherwise the page is printed in portrait mode.
void FileComponent::PrintToPdf(bool enableLandscape)
{
    WCHAR defaultName[MAX_PATH] = L"WebView2_PrintedPdf.pdf";
    OPENFILENAME openFileName = CreateOpenFileName(defaultName, L"PDF File\0*.pdf\0");
    if (GetSaveFileName(&openFileName))
    {
        wil::com_ptr<ICoreWebView2ExperimentalPrintSettings> printSettings = nullptr;
        if (enableLandscape)
        {
            wil::com_ptr<ICoreWebView2ExperimentalEnvironment7> webviewEnvironment7;
            CHECK_FAILURE(m_appWindow->GetWebViewEnvironment()->QueryInterface(
                IID_PPV_ARGS(&webviewEnvironment7)));
            if (webviewEnvironment7)
            {
                CHECK_FAILURE(webviewEnvironment7->CreatePrintSettings(&printSettings));
                CHECK_FAILURE(
                    printSettings->put_Orientation(COREWEBVIEW2_PRINT_ORIENTATION_LANDSCAPE));
            }
        }

        wil::com_ptr<ICoreWebView2Experimental7> webviewExperimental7;
        CHECK_FAILURE(m_webView->QueryInterface(IID_PPV_ARGS(&webviewExperimental7)));
        if (webviewExperimental7)
        {
            m_printToPdfInProgress = true;
            CHECK_FAILURE(webviewExperimental7->PrintToPdf(
                openFileName.lpstrFile, printSettings.get(),
                Callback<ICoreWebView2ExperimentalPrintToPdfCompletedHandler>(
                    [this](HRESULT errorCode, BOOL isSuccessful) -> HRESULT {
                        CHECK_FAILURE(errorCode);
                        m_printToPdfInProgress = false;
                        auto showDialog = [isSuccessful] {
                            MessageBox(
                                nullptr,
                                (isSuccessful) ? L"Print to PDF succeeded"
                                               : L"Print to PDF failed",
                                L"Print to PDF Completed", MB_OK);
                        };
                        m_appWindow->RunAsync([showDialog]() { showDialog(); });
                        return S_OK;
                    })
                    .Get()));
        }
    }
}
```

