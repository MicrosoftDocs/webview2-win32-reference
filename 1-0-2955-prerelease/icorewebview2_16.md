---
description: A continuation of the ICoreWebView2 interface to support printing.
title: WebView2 Win32 C++ ICoreWebView2_16
ms.date: 11/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_16
topic_type: 
- APIRef
api_name:
- ICoreWebView2_16
- ICoreWebView2_16.Print
- ICoreWebView2_16.PrintToPdfStream
- ICoreWebView2_16.ShowPrintUI
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_16

```
interface ICoreWebView2_16
  : public ICoreWebView2_15
```

A continuation of the [ICoreWebView2](icorewebview2.md#icorewebview2) interface to support printing.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Print](#print) | Print the current web page asynchronously to the specified printer with the provided settings.
[PrintToPdfStream](#printtopdfstream) | Provides the Pdf data of current web page asynchronously for the provided settings.
[ShowPrintUI](#showprintui) | Opens the print dialog to print the current web page.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### Print

Print the current web page asynchronously to the specified printer with the provided settings.

> public HRESULT [Print](#print)([ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) * printSettings, [ICoreWebView2PrintCompletedHandler](icorewebview2printcompletedhandler.md#icorewebview2printcompletedhandler) * handler)

See [ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) for description of settings. Passing nullptr for `printSettings` results in default print settings used.

The handler will return `errorCode` as `S_OK` and `printStatus` as COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE if `printerName` doesn't match with the name of any installed printers on the user OS. The handler will return `errorCode` as `E_INVALIDARG` and `printStatus` as COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR if the caller provides invalid settings for a given printer.

The async `Print` operation completes when it finishes printing to the printer. At this time the [ICoreWebView2PrintCompletedHandler](icorewebview2printcompletedhandler.md#icorewebview2printcompletedhandler) is invoked. Only one `Printing` operation can be in progress at a time. If `Print` is called while a `Print` or `PrintToPdf` or `PrintToPdfStream` or `ShowPrintUI` job is in progress, the completed handler is immediately invoked with `E_ABORT` and `printStatus` is COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR. This is only for printing operation on one webview.

errorCode   |printStatus   |Notes
--------- | --------- | ---------
S_OK   |COREWEBVIEW2_PRINT_STATUS_SUCCEEDED   |Print operation succeeded.
S_OK   |COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE   |If specified printer is not found or printer status is not available, offline or error state.
S_OK   |COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR   |Print operation is failed.
E_INVALIDARG   |COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR   |If the caller provides invalid settings for the specified printer.
E_ABORT   |COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR   |Print operation is failed as printing job already in progress.

```cpp
// This example prints the current web page to a specified printer with the settings.
bool AppWindow::PrintToPrinter()
{
    std::wstring printerName = GetPrinterName();
    // Host apps custom print settings based on the user selection.
    SamplePrintSettings samplePrintSettings = GetSelectedPrinterPrintSettings(printerName);

    wil::com_ptr<ICoreWebView2_16> webView2_16;
    CHECK_FAILURE(m_webView->QueryInterface(IID_PPV_ARGS(&webView2_16)));

    wil::com_ptr<ICoreWebView2Environment6> webviewEnvironment6;
    CHECK_FAILURE(m_webViewEnvironment->QueryInterface(IID_PPV_ARGS(&webviewEnvironment6)));

    wil::com_ptr<ICoreWebView2PrintSettings> printSettings;
    CHECK_FAILURE(webviewEnvironment6->CreatePrintSettings(&printSettings));

    wil::com_ptr<ICoreWebView2PrintSettings2> printSettings2;
    CHECK_FAILURE(printSettings->QueryInterface(IID_PPV_ARGS(&printSettings2)));

    CHECK_FAILURE(printSettings->put_Orientation(samplePrintSettings.Orientation));
    CHECK_FAILURE(printSettings2->put_Copies(samplePrintSettings.Copies));
    CHECK_FAILURE(printSettings2->put_PagesPerSide(samplePrintSettings.PagesPerSide));
    CHECK_FAILURE(printSettings2->put_PageRanges(samplePrintSettings.Pages.c_str()));
    if (samplePrintSettings.Media == COREWEBVIEW2_PRINT_MEDIA_SIZE_CUSTOM)
    {
        CHECK_FAILURE(printSettings->put_PageWidth(samplePrintSettings.PaperWidth));
        CHECK_FAILURE(printSettings->put_PageHeight(samplePrintSettings.PaperHeight));
    }
    CHECK_FAILURE(printSettings2->put_ColorMode(samplePrintSettings.ColorMode));
    CHECK_FAILURE(printSettings2->put_Collation(samplePrintSettings.Collation));
    CHECK_FAILURE(printSettings2->put_Duplex(samplePrintSettings.Duplex));
    CHECK_FAILURE(printSettings->put_ScaleFactor(samplePrintSettings.ScaleFactor));
    CHECK_FAILURE(
        printSettings->put_ShouldPrintBackgrounds(samplePrintSettings.PrintBackgrounds));
    CHECK_FAILURE(
        printSettings->put_ShouldPrintBackgrounds(samplePrintSettings.PrintBackgrounds));
    CHECK_FAILURE(
        printSettings->put_ShouldPrintHeaderAndFooter(samplePrintSettings.HeaderAndFooter));
    CHECK_FAILURE(printSettings->put_HeaderTitle(samplePrintSettings.HeaderTitle.c_str()));
    CHECK_FAILURE(printSettings->put_FooterUri(samplePrintSettings.FooterUri.c_str()));
    CHECK_FAILURE(printSettings2->put_PrinterName(printerName.c_str()));

    wil::unique_cotaskmem_string title;
    CHECK_FAILURE(m_webView->get_DocumentTitle(&title));

    CHECK_FAILURE(webView2_16->Print(
        printSettings.get(),
        Callback<ICoreWebView2PrintCompletedHandler>(
            [title = std::move(title),
             this](HRESULT errorCode, COREWEBVIEW2_PRINT_STATUS printStatus) -> HRESULT
            {
                std::wstring message = L"";
                if (errorCode == S_OK && printStatus == COREWEBVIEW2_PRINT_STATUS_SUCCEEDED)
                {
                    message = L"Printing " + std::wstring(title.get()) +
                              L" document to printer is succeeded";
                }
                else if (
                    errorCode == S_OK &&
                    printStatus == COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE)
                {
                    message = L"Selected printer is not found, not available, offline or "
                              L"error state.";
                }
                else if (errorCode == E_INVALIDARG)
                {
                    message = L"Invalid settings provided for the specified printer";
                }
                else if (errorCode == E_ABORT)
                {
                    message = L"Printing " + std::wstring(title.get()) +
                              L" document already in progress";
                }
                else
                {
                    message = L"Printing " + std::wstring(title.get()) +
                              L" document to printer is failed";
                }

                AsyncMessageBox(message, L"Print to printer");

                return S_OK;
            })
            .Get()));
    return true;
}
```

#### PrintToPdfStream

Provides the Pdf data of current web page asynchronously for the provided settings.

> public HRESULT [PrintToPdfStream](#printtopdfstream)([ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) * printSettings, [ICoreWebView2PrintToPdfStreamCompletedHandler](icorewebview2printtopdfstreamcompletedhandler.md#icorewebview2printtopdfstreamcompletedhandler) * handler)

Stream will be rewound to the start of the pdf data.

See [ICoreWebView2PrintSettings](icorewebview2printsettings.md#icorewebview2printsettings) for description of settings. Passing nullptr for `printSettings` results in default print settings used.

The async `PrintToPdfStream` operation completes when it finishes writing to the stream. At this time the [ICoreWebView2PrintToPdfStreamCompletedHandler](icorewebview2printtopdfstreamcompletedhandler.md#icorewebview2printtopdfstreamcompletedhandler) is invoked. Only one `Printing` operation can be in progress at a time. If `PrintToPdfStream` is called while a `PrintToPdfStream` or `PrintToPdf` or `Print` or `ShowPrintUI` job is in progress, the completed handler is immediately invoked with `E_ABORT`. This is only for printing operation on one webview.

```cpp
// This example prints the Pdf data of the current page to a stream.
bool AppWindow::PrintToPdfStream()
{
    wil::com_ptr<ICoreWebView2_16> webView2_16;
    CHECK_FAILURE(m_webView->QueryInterface(IID_PPV_ARGS(&webView2_16)));

    wil::unique_cotaskmem_string title;
    CHECK_FAILURE(m_webView->get_DocumentTitle(&title));

    // Passing nullptr for `ICoreWebView2PrintSettings` results in default print settings used.
    CHECK_FAILURE(webView2_16->PrintToPdfStream(
        nullptr,
        Callback<ICoreWebView2PrintToPdfStreamCompletedHandler>(
            [title = std::move(title), this](HRESULT errorCode, IStream* pdfData) -> HRESULT
            {
                DisplayPdfDataInPrintDialog(pdfData);

                std::wstring message =
                    L"Printing " + std::wstring(title.get()) + L" document to PDF Stream " +
                    ((errorCode == S_OK && pdfData != nullptr) ? L"succedded" : L"failed");

                AsyncMessageBox(message, L"Print to PDF Stream");

                return S_OK;
            })
            .Get()));
    return true;
}
```

#### ShowPrintUI

Opens the print dialog to print the current web page.

> public HRESULT [ShowPrintUI](#showprintui)(COREWEBVIEW2_PRINT_DIALOG_KIND printDialogKind)

See `COREWEBVIEW2_PRINT_DIALOG_KIND` for descriptions of print dialog kinds.

Invoking browser or system print dialog doesn't open new print dialog if it is already open.

```cpp
// Shows the user a print dialog. If `printDialogKind` is
// COREWEBVIEW2_PRINT_DIALOG_KIND_BROWSER, opens a browser print preview dialog,
// COREWEBVIEW2_PRINT_DIALOG_KIND_SYSTEM opens a system print dialog.
bool AppWindow::ShowPrintUI(COREWEBVIEW2_PRINT_DIALOG_KIND printDialogKind)
{
    auto webView2_16 = m_webView.try_query<ICoreWebView2_16>();
    CHECK_FEATURE_RETURN(webView2_16);
    CHECK_FAILURE(webView2_16->ShowPrintUI(printDialogKind));
    return true;
}
```

