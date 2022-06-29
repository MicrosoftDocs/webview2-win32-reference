---
description: Settings used by the `PrintToPdf` method.
title: WebView2 Win32 C++ ICoreWebView2PrintSettings
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintSettings
---

# interface ICoreWebView2PrintSettings

```
interface ICoreWebView2PrintSettings
  : public IUnknown
```

Settings used by the `PrintToPdf` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FooterUri](#get_footeruri) | The URI in the footer if `ShouldPrintHeaderAndFooter` is `TRUE`.
[get_HeaderTitle](#get_headertitle) | The title in the header if `ShouldPrintHeaderAndFooter` is `TRUE`.
[get_MarginBottom](#get_marginbottom) | The bottom margin in inches. The default is 1 cm, or ~0.4 inches.
[get_MarginLeft](#get_marginleft) | The left margin in inches. The default is 1 cm, or ~0.4 inches.
[get_MarginRight](#get_marginright) | The right margin in inches. The default is 1 cm, or ~0.4 inches.
[get_MarginTop](#get_margintop) | The top margin in inches. The default is 1 cm, or ~0.4 inches.
[get_Orientation](#get_orientation) | The orientation can be portrait or landscape.
[get_PageHeight](#get_pageheight) | The page height in inches. The default height is 11 inches.
[get_PageWidth](#get_pagewidth) | The page width in inches. The default width is 8.5 inches.
[get_ScaleFactor](#get_scalefactor) | The scale factor is a value between 0.1 and 2.0. The default is 1.0.
[get_ShouldPrintBackgrounds](#get_shouldprintbackgrounds) | `TRUE` if background colors and images should be printed.
[get_ShouldPrintHeaderAndFooter](#get_shouldprintheaderandfooter) | `TRUE` if header and footer should be printed.
[get_ShouldPrintSelectionOnly](#get_shouldprintselectiononly) | `TRUE` if only the current end user's selection of HTML in the document should be printed.
[put_FooterUri](#put_footeruri) | Set the `FooterUri` property.
[put_HeaderTitle](#put_headertitle) | Set the `HeaderTitle` property.
[put_MarginBottom](#put_marginbottom) | Sets the `MarginBottom` property.
[put_MarginLeft](#put_marginleft) | Sets the `MarginLeft` property.
[put_MarginRight](#put_marginright) | Set the `MarginRight` property.A margin cannot be less than zero.
[put_MarginTop](#put_margintop) | Sets the `MarginTop` property.
[put_Orientation](#put_orientation) | Sets the `Orientation` property.
[put_PageHeight](#put_pageheight) | Sets the `PageHeight` property.
[put_PageWidth](#put_pagewidth) | Sets the `PageWidth` property.
[put_ScaleFactor](#put_scalefactor) | Sets the `ScaleFactor` property.
[put_ShouldPrintBackgrounds](#put_shouldprintbackgrounds) | Set the `ShouldPrintBackgrounds` property.
[put_ShouldPrintHeaderAndFooter](#put_shouldprintheaderandfooter) | Set the `ShouldPrintHeaderAndFooter` property.
[put_ShouldPrintSelectionOnly](#put_shouldprintselectiononly) | Set the `ShouldPrintSelectionOnly` property.

Other programmatic printing is not currently supported.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1020.30
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### get_FooterUri

The URI in the footer if `ShouldPrintHeaderAndFooter` is `TRUE`.

> public HRESULT [get_FooterUri](#get_footeruri)(LPWSTR * footerUri)

The default value is the current URI.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_HeaderTitle

The title in the header if `ShouldPrintHeaderAndFooter` is `TRUE`.

> public HRESULT [get_HeaderTitle](#get_headertitle)(LPWSTR * headerTitle)

The default value is the title of the current document.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_MarginBottom

The bottom margin in inches. The default is 1 cm, or ~0.4 inches.

> public HRESULT [get_MarginBottom](#get_marginbottom)(double * marginBottom)

#### get_MarginLeft

The left margin in inches. The default is 1 cm, or ~0.4 inches.

> public HRESULT [get_MarginLeft](#get_marginleft)(double * marginLeft)

#### get_MarginRight

The right margin in inches. The default is 1 cm, or ~0.4 inches.

> public HRESULT [get_MarginRight](#get_marginright)(double * marginRight)

#### get_MarginTop

The top margin in inches. The default is 1 cm, or ~0.4 inches.

> public HRESULT [get_MarginTop](#get_margintop)(double * marginTop)

#### get_Orientation

The orientation can be portrait or landscape.

> public HRESULT [get_Orientation](#get_orientation)(COREWEBVIEW2_PRINT_ORIENTATION * orientation)

The default orientation is portrait. See `COREWEBVIEW2_PRINT_ORIENTATION`.

#### get_PageHeight

The page height in inches. The default height is 11 inches.

> public HRESULT [get_PageHeight](#get_pageheight)(double * pageHeight)

#### get_PageWidth

The page width in inches. The default width is 8.5 inches.

> public HRESULT [get_PageWidth](#get_pagewidth)(double * pageWidth)

#### get_ScaleFactor

The scale factor is a value between 0.1 and 2.0. The default is 1.0.

> public HRESULT [get_ScaleFactor](#get_scalefactor)(double * scaleFactor)

#### get_ShouldPrintBackgrounds

`TRUE` if background colors and images should be printed.

> public HRESULT [get_ShouldPrintBackgrounds](#get_shouldprintbackgrounds)(BOOL * shouldPrintBackgrounds)

The default value is `FALSE`.

#### get_ShouldPrintHeaderAndFooter

`TRUE` if header and footer should be printed.

> public HRESULT [get_ShouldPrintHeaderAndFooter](#get_shouldprintheaderandfooter)(BOOL * shouldPrintHeaderAndFooter)

The default value is `FALSE`. The header consists of the date and time of printing, and the title of the page. The footer consists of the URI and page number. The height of the header and footer is 0.5 cm, or ~0.2 inches.

#### get_ShouldPrintSelectionOnly

`TRUE` if only the current end user's selection of HTML in the document should be printed.

> public HRESULT [get_ShouldPrintSelectionOnly](#get_shouldprintselectiononly)(BOOL * shouldPrintSelectionOnly)

The default value is `FALSE`.

#### put_FooterUri

Set the `FooterUri` property.

> public HRESULT [put_FooterUri](#put_footeruri)(LPCWSTR footerUri)

If an empty string or null value is provided, no URI is shown in the footer.

#### put_HeaderTitle

Set the `HeaderTitle` property.

> public HRESULT [put_HeaderTitle](#put_headertitle)(LPCWSTR headerTitle)

If an empty string or null value is provided, no title is shown in the header.

#### put_MarginBottom

Sets the `MarginBottom` property.

> public HRESULT [put_MarginBottom](#put_marginbottom)(double marginBottom)

A margin cannot be less than zero. Returns `E_INVALIDARG` if an invalid value is provided, and the current value is not changed.

#### put_MarginLeft

Sets the `MarginLeft` property.

> public HRESULT [put_MarginLeft](#put_marginleft)(double marginLeft)

A margin cannot be less than zero. Returns `E_INVALIDARG` if an invalid value is provided, and the current value is not changed.

#### put_MarginRight

Set the `MarginRight` property.A margin cannot be less than zero.

> public HRESULT [put_MarginRight](#put_marginright)(double marginRight)

Returns `E_INVALIDARG` if an invalid value is provided, and the current value is not changed.

#### put_MarginTop

Sets the `MarginTop` property.

> public HRESULT [put_MarginTop](#put_margintop)(double marginTop)

A margin cannot be less than zero. Returns `E_INVALIDARG` if an invalid value is provided, and the current value is not changed.

#### put_Orientation

Sets the `Orientation` property.

> public HRESULT [put_Orientation](#put_orientation)(COREWEBVIEW2_PRINT_ORIENTATION orientation)

#### put_PageHeight

Sets the `PageHeight` property.

> public HRESULT [put_PageHeight](#put_pageheight)(double pageHeight)

Returns `E_INVALIDARG` if the page height is less than or equal to zero, and the current value is not changed.

#### put_PageWidth

Sets the `PageWidth` property.

> public HRESULT [put_PageWidth](#put_pagewidth)(double pageWidth)

Returns `E_INVALIDARG` if the page width is less than or equal to zero, and the current value is not changed.

#### put_ScaleFactor

Sets the `ScaleFactor` property.

> public HRESULT [put_ScaleFactor](#put_scalefactor)(double scaleFactor)

Returns `E_INVALIDARG` if an invalid value is provided, and the current value is not changed.

#### put_ShouldPrintBackgrounds

Set the `ShouldPrintBackgrounds` property.

> public HRESULT [put_ShouldPrintBackgrounds](#put_shouldprintbackgrounds)(BOOL shouldPrintBackgrounds)

#### put_ShouldPrintHeaderAndFooter

Set the `ShouldPrintHeaderAndFooter` property.

> public HRESULT [put_ShouldPrintHeaderAndFooter](#put_shouldprintheaderandfooter)(BOOL shouldPrintHeaderAndFooter)

#### put_ShouldPrintSelectionOnly

Set the `ShouldPrintSelectionOnly` property.

> public HRESULT [put_ShouldPrintSelectionOnly](#put_shouldprintselectiononly)(BOOL shouldPrintSelectionOnly)

