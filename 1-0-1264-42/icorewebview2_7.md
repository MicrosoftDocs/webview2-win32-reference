---
description: This interface is an extension of ICoreWebView2_6 that supports printing to PDF.
title: WebView2 Win32 C++ ICoreWebView2_7
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_7
---

# interface ICoreWebView2_7

```
interface ICoreWebView2_7
  : public ICoreWebView2_6
```

This interface is an extension of [ICoreWebView2_6](icorewebview2_6.md) that supports printing to PDF.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PrintToPdf](#printtopdf) | Print the current page to PDF asynchronously with the provided settings.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1020.30
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### PrintToPdf

Print the current page to PDF asynchronously with the provided settings.

> public HRESULT [PrintToPdf](#printtopdf)(LPCWSTR resultFilePath, [ICoreWebView2PrintSettings](icorewebview2printsettings.md) * printSettings, [ICoreWebView2PrintToPdfCompletedHandler](icorewebview2printtopdfcompletedhandler.md) * handler)

See [ICoreWebView2PrintSettings](icorewebview2printsettings.md) for description of settings. Passing nullptr for `printSettings` results in default print settings used.

Use `resultFilePath` to specify the path to the PDF file. The host should provide an absolute path, including file name. If the path points to an existing file, the file will be overwritten. If the path is not valid, the method fails with `E_INVALIDARG`.

The async `PrintToPdf` operation completes when the data has been written to the PDF file. At this time the [ICoreWebView2PrintToPdfCompletedHandler](icorewebview2printtopdfcompletedhandler.md) is invoked. If the application exits before printing is complete, the file is not saved. Only one `PrintToPdf` operation can be in progress at a time. If `PrintToPdf` is called while a print to PDF job is in progress, the completed handler is immediately invoked with `isSuccessful` set to FALSE.

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
        wil::com_ptr<ICoreWebView2PrintSettings> printSettings = nullptr;
        if (enableLandscape)
        {
            wil::com_ptr<ICoreWebView2Environment6> webviewEnvironment6;
            CHECK_FAILURE(m_appWindow->GetWebViewEnvironment()->QueryInterface(
                IID_PPV_ARGS(&webviewEnvironment6)));
            if (webviewEnvironment6)
            {
                CHECK_FAILURE(webviewEnvironment6->CreatePrintSettings(&printSettings));
                CHECK_FAILURE(
                    printSettings->put_Orientation(COREWEBVIEW2_PRINT_ORIENTATION_LANDSCAPE));
            }
        }

        wil::com_ptr<ICoreWebView2_7> webview2_7;
        CHECK_FAILURE(m_webView->QueryInterface(IID_PPV_ARGS(&webview2_7)));
        if (webview2_7)
        {
            m_printToPdfInProgress = true;
            CHECK_FAILURE(webview2_7->PrintToPdf(
                openFileName.lpstrFile, printSettings.get(),
                Callback<ICoreWebView2PrintToPdfCompletedHandler>(
                    [this](HRESULT errorCode, BOOL isSuccessful) -> HRESULT {
                        CHECK_FAILURE(errorCode);
                        m_printToPdfInProgress = false;
                        m_appWindow->AsyncMessageBox(
                            (isSuccessful) ? L"Print to PDF succeeded"
                                           : L"Print to PDF failed",
                            L"Print to PDF Completed");
                        return S_OK;
                    })
                    .Get()));
        }
    }
}
```

