---
description: This is an extension of the ICoreWebView2Settings Experimental interface for HiddenPdfToolbarItems.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings6
ms.date: 02/09/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings6
---

# interface ICoreWebView2ExperimentalSettings6

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings6
  : public IUnknown
```

This is an extension of the [ICoreWebView2Settings](icorewebview2settings.md) Experimental interface for HiddenPdfToolbarItems.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HiddenPdfToolbarItems](#get_hiddenpdftoolbaritems) | `HiddenPdfToolbarItems` is used to customize the PDF toolbar items.
[put_HiddenPdfToolbarItems](#put_hiddenpdftoolbaritems) | Set the `HiddenPdfToolbarItems` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.955

## Members

#### get_HiddenPdfToolbarItems

`HiddenPdfToolbarItems` is used to customize the PDF toolbar items.

> public HRESULT [get_HiddenPdfToolbarItems](#get_hiddenpdftoolbaritems)(COREWEBVIEW2_PDF_TOOLBAR_ITEMS * hidden_pdf_toolbar_items)

By default, it is COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE and so it displays all of the items. Changes to this property apply to all CoreWebView2s in the same environment and using the same profile. Changes to this setting apply only after the next navigation. 
```cpp
            wil::com_ptr<ICoreWebView2ExperimentalSettings6> experimentalSettings6;
            experimentalSettings6 = m_settings.try_query<ICoreWebView2ExperimentalSettings6>();
            CHECK_FEATURE_RETURN(experimentalSettings6);

            COREWEBVIEW2_PDF_TOOLBAR_ITEMS hiddenPdfToolbarItems;
            CHECK_FAILURE(
                experimentalSettings6->get_HiddenPdfToolbarItems(&hiddenPdfToolbarItems));
            if (hiddenPdfToolbarItems ==
                COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE)
            {
                CHECK_FAILURE(experimentalSettings6->put_HiddenPdfToolbarItems(
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PRINT |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE));
                MessageBox(
                    nullptr,
                    L"PDF toolbar print and save buttons are hidden after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(experimentalSettings6->put_HiddenPdfToolbarItems(
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE));
                MessageBox(
                    nullptr,
                    L"PDF toolbar print and save buttons are shown after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

#### put_HiddenPdfToolbarItems

Set the `HiddenPdfToolbarItems` property.

> public HRESULT [put_HiddenPdfToolbarItems](#put_hiddenpdftoolbaritems)(COREWEBVIEW2_PDF_TOOLBAR_ITEMS hidden_pdf_toolbar_items)

