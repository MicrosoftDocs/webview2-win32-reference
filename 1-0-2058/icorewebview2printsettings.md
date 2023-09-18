---
description: 
title: WebView2 Win32 C++ ICoreWebView2PrintSettings
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintSettings
topic_type: 
- APIRef
api_name:
- ICoreWebView2PrintSettings
- ICoreWebView2PrintSettings.get_FooterUri
- ICoreWebView2PrintSettings.get_HeaderTitle
- ICoreWebView2PrintSettings.get_MarginBottom
- ICoreWebView2PrintSettings.get_MarginLeft
- ICoreWebView2PrintSettings.get_MarginRight
- ICoreWebView2PrintSettings.get_MarginTop
- ICoreWebView2PrintSettings.get_Orientation
- ICoreWebView2PrintSettings.get_PageHeight
- ICoreWebView2PrintSettings.get_PageWidth
- ICoreWebView2PrintSettings.get_ScaleFactor
- ICoreWebView2PrintSettings.get_ShouldPrintBackgrounds
- ICoreWebView2PrintSettings.get_ShouldPrintHeaderAndFooter
- ICoreWebView2PrintSettings.get_ShouldPrintSelectionOnly
- ICoreWebView2PrintSettings.put_FooterUri
- ICoreWebView2PrintSettings.put_HeaderTitle
- ICoreWebView2PrintSettings.put_MarginBottom
- ICoreWebView2PrintSettings.put_MarginLeft
- ICoreWebView2PrintSettings.put_MarginRight
- ICoreWebView2PrintSettings.put_MarginTop
- ICoreWebView2PrintSettings.put_Orientation
- ICoreWebView2PrintSettings.put_PageHeight
- ICoreWebView2PrintSettings.put_PageWidth
- ICoreWebView2PrintSettings.put_ScaleFactor
- ICoreWebView2PrintSettings.put_ShouldPrintBackgrounds
- ICoreWebView2PrintSettings.put_ShouldPrintHeaderAndFooter
- ICoreWebView2PrintSettings.put_ShouldPrintSelectionOnly
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PrintSettings

```
interface ICoreWebView2PrintSettings
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FooterUri](#get_footeruri) | Gets the `FooterUri` property.
[get_HeaderTitle](#get_headertitle) | Gets the `HeaderTitle` property.
[get_MarginBottom](#get_marginbottom) | Gets the `MarginBottom` property.
[get_MarginLeft](#get_marginleft) | Gets the `MarginLeft` property.
[get_MarginRight](#get_marginright) | Gets the `MarginRight` property.
[get_MarginTop](#get_margintop) | Gets the `MarginTop` property.
[get_Orientation](#get_orientation) | Gets the `Orientation` property.
[get_PageHeight](#get_pageheight) | Gets the `PageHeight` property.
[get_PageWidth](#get_pagewidth) | Gets the `PageWidth` property.
[get_ScaleFactor](#get_scalefactor) | Gets the `ScaleFactor` property.
[get_ShouldPrintBackgrounds](#get_shouldprintbackgrounds) | Gets the `ShouldPrintBackgrounds` property.
[get_ShouldPrintHeaderAndFooter](#get_shouldprintheaderandfooter) | Gets the `ShouldPrintHeaderAndFooter` property.
[get_ShouldPrintSelectionOnly](#get_shouldprintselectiononly) | Gets the `ShouldPrintSelectionOnly` property.
[put_FooterUri](#put_footeruri) | Sets the `FooterUri` property.
[put_HeaderTitle](#put_headertitle) | Sets the `HeaderTitle` property.
[put_MarginBottom](#put_marginbottom) | Sets the `MarginBottom` property.
[put_MarginLeft](#put_marginleft) | Sets the `MarginLeft` property.
[put_MarginRight](#put_marginright) | Sets the `MarginRight` property.
[put_MarginTop](#put_margintop) | Sets the `MarginTop` property.
[put_Orientation](#put_orientation) | Sets the `Orientation` property.
[put_PageHeight](#put_pageheight) | Sets the `PageHeight` property.
[put_PageWidth](#put_pagewidth) | Sets the `PageWidth` property.
[put_ScaleFactor](#put_scalefactor) | Sets the `ScaleFactor` property.
[put_ShouldPrintBackgrounds](#put_shouldprintbackgrounds) | Sets the `ShouldPrintBackgrounds` property.
[put_ShouldPrintHeaderAndFooter](#put_shouldprintheaderandfooter) | Sets the `ShouldPrintHeaderAndFooter` property.
[put_ShouldPrintSelectionOnly](#put_shouldprintselectiononly) | Sets the `ShouldPrintSelectionOnly` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1020.30
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### get_FooterUri

Gets the `FooterUri` property.

> public HRESULT [get_FooterUri](#get_footeruri)(LPWSTR * value)

#### get_HeaderTitle

Gets the `HeaderTitle` property.

> public HRESULT [get_HeaderTitle](#get_headertitle)(LPWSTR * value)

#### get_MarginBottom

Gets the `MarginBottom` property.

> public HRESULT [get_MarginBottom](#get_marginbottom)(double * value)

#### get_MarginLeft

Gets the `MarginLeft` property.

> public HRESULT [get_MarginLeft](#get_marginleft)(double * value)

#### get_MarginRight

Gets the `MarginRight` property.

> public HRESULT [get_MarginRight](#get_marginright)(double * value)

#### get_MarginTop

Gets the `MarginTop` property.

> public HRESULT [get_MarginTop](#get_margintop)(double * value)

#### get_Orientation

Gets the `Orientation` property.

> public HRESULT [get_Orientation](#get_orientation)(COREWEBVIEW2_PRINT_ORIENTATION * value)

#### get_PageHeight

Gets the `PageHeight` property.

> public HRESULT [get_PageHeight](#get_pageheight)(double * value)

#### get_PageWidth

Gets the `PageWidth` property.

> public HRESULT [get_PageWidth](#get_pagewidth)(double * value)

#### get_ScaleFactor

Gets the `ScaleFactor` property.

> public HRESULT [get_ScaleFactor](#get_scalefactor)(double * value)

#### get_ShouldPrintBackgrounds

Gets the `ShouldPrintBackgrounds` property.

> public HRESULT [get_ShouldPrintBackgrounds](#get_shouldprintbackgrounds)(BOOL * value)

#### get_ShouldPrintHeaderAndFooter

Gets the `ShouldPrintHeaderAndFooter` property.

> public HRESULT [get_ShouldPrintHeaderAndFooter](#get_shouldprintheaderandfooter)(BOOL * value)

#### get_ShouldPrintSelectionOnly

Gets the `ShouldPrintSelectionOnly` property.

> public HRESULT [get_ShouldPrintSelectionOnly](#get_shouldprintselectiononly)(BOOL * value)

#### put_FooterUri

Sets the `FooterUri` property.

> public HRESULT [put_FooterUri](#put_footeruri)(LPCWSTR value)

#### put_HeaderTitle

Sets the `HeaderTitle` property.

> public HRESULT [put_HeaderTitle](#put_headertitle)(LPCWSTR value)

#### put_MarginBottom

Sets the `MarginBottom` property.

> public HRESULT [put_MarginBottom](#put_marginbottom)(double value)

#### put_MarginLeft

Sets the `MarginLeft` property.

> public HRESULT [put_MarginLeft](#put_marginleft)(double value)

#### put_MarginRight

Sets the `MarginRight` property.

> public HRESULT [put_MarginRight](#put_marginright)(double value)

#### put_MarginTop

Sets the `MarginTop` property.

> public HRESULT [put_MarginTop](#put_margintop)(double value)

#### put_Orientation

Sets the `Orientation` property.

> public HRESULT [put_Orientation](#put_orientation)(COREWEBVIEW2_PRINT_ORIENTATION value)

#### put_PageHeight

Sets the `PageHeight` property.

> public HRESULT [put_PageHeight](#put_pageheight)(double value)

#### put_PageWidth

Sets the `PageWidth` property.

> public HRESULT [put_PageWidth](#put_pagewidth)(double value)

#### put_ScaleFactor

Sets the `ScaleFactor` property.

> public HRESULT [put_ScaleFactor](#put_scalefactor)(double value)

#### put_ShouldPrintBackgrounds

Sets the `ShouldPrintBackgrounds` property.

> public HRESULT [put_ShouldPrintBackgrounds](#put_shouldprintbackgrounds)(BOOL value)

#### put_ShouldPrintHeaderAndFooter

Sets the `ShouldPrintHeaderAndFooter` property.

> public HRESULT [put_ShouldPrintHeaderAndFooter](#put_shouldprintheaderandfooter)(BOOL value)

#### put_ShouldPrintSelectionOnly

Sets the `ShouldPrintSelectionOnly` property.

> public HRESULT [put_ShouldPrintSelectionOnly](#put_shouldprintselectiononly)(BOOL value)

