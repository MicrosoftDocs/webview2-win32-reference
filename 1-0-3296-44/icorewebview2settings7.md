---
description: A continuation of the ICoreWebView2Settings interface to hide Pdf toolbar items.
title: WebView2 Win32 C++ ICoreWebView2Settings7
ms.date: 05/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings7
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings7
- ICoreWebView2Settings7.get_HiddenPdfToolbarItems
- ICoreWebView2Settings7.put_HiddenPdfToolbarItems
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings7

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Settings7
  : public ICoreWebView2Settings6
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface to hide Pdf toolbar items.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HiddenPdfToolbarItems](#get_hiddenpdftoolbaritems) | Gets the `HiddenPdfToolbarItems` property.
[put_HiddenPdfToolbarItems](#put_hiddenpdftoolbaritems) | `HiddenPdfToolbarItems` is used to customize the PDF toolbar items.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_HiddenPdfToolbarItems

Gets the `HiddenPdfToolbarItems` property.

> public HRESULT [get_HiddenPdfToolbarItems](#get_hiddenpdftoolbaritems)(COREWEBVIEW2_PDF_TOOLBAR_ITEMS * value)

#### put_HiddenPdfToolbarItems

`HiddenPdfToolbarItems` is used to customize the PDF toolbar items.

> public HRESULT [put_HiddenPdfToolbarItems](#put_hiddenpdftoolbaritems)(COREWEBVIEW2_PDF_TOOLBAR_ITEMS value)

By default, it is COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE and so it displays all of the items. Changes to this property apply to all CoreWebView2s in the same environment and using the same profile. Changes to this setting apply only after the next navigation. 
```cpp
            CHECK_FEATURE_RETURN(m_settings7);

            COREWEBVIEW2_PDF_TOOLBAR_ITEMS hiddenPdfToolbarItems;
            CHECK_FAILURE(m_settings7->get_HiddenPdfToolbarItems(&hiddenPdfToolbarItems));
            if (hiddenPdfToolbarItems ==
                COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE)
            {
                CHECK_FAILURE(
                    m_settings7->put_HiddenPdfToolbarItems(
                        COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PRINT |
                        COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE) |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_BOOKMARKS |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_FIT_PAGE |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PAGE_LAYOUT |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ROTATE |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SEARCH |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ZOOM_IN |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_ZOOM_OUT |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_SAVE_AS |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::
                        COREWEBVIEW2_PDF_TOOLBAR_ITEMS_PAGE_SELECTOR |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_FULL_SCREEN |
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::
                        COREWEBVIEW2_PDF_TOOLBAR_ITEMS_MORE_SETTINGS);
                MessageBox(
                    nullptr,
                    L"PDF toolbar print and save buttons are hidden after the next navigation.",
                    L"Settings change", MB_OK);
            }
            else
            {
                CHECK_FAILURE(m_settings7->put_HiddenPdfToolbarItems(
                    COREWEBVIEW2_PDF_TOOLBAR_ITEMS::COREWEBVIEW2_PDF_TOOLBAR_ITEMS_NONE));
                MessageBox(
                    nullptr,
                    L"PDF toolbar print and save buttons are shown after the next navigation.",
                    L"Settings change", MB_OK);
            }
```

