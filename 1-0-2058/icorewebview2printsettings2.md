---
description: 
title: WebView2 Win32 C++ ICoreWebView2PrintSettings2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintSettings2
topic_type: 
- APIRef
api_name:
- ICoreWebView2PrintSettings2
- ICoreWebView2PrintSettings2.get_Collation
- ICoreWebView2PrintSettings2.get_ColorMode
- ICoreWebView2PrintSettings2.get_Copies
- ICoreWebView2PrintSettings2.get_Duplex
- ICoreWebView2PrintSettings2.get_MediaSize
- ICoreWebView2PrintSettings2.get_PageRanges
- ICoreWebView2PrintSettings2.get_PagesPerSide
- ICoreWebView2PrintSettings2.get_PrinterName
- ICoreWebView2PrintSettings2.put_Collation
- ICoreWebView2PrintSettings2.put_ColorMode
- ICoreWebView2PrintSettings2.put_Copies
- ICoreWebView2PrintSettings2.put_Duplex
- ICoreWebView2PrintSettings2.put_MediaSize
- ICoreWebView2PrintSettings2.put_PageRanges
- ICoreWebView2PrintSettings2.put_PagesPerSide
- ICoreWebView2PrintSettings2.put_PrinterName
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PrintSettings2

```
interface ICoreWebView2PrintSettings2
  : public ICoreWebView2PrintSettings
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Collation](#get_collation) | Gets the `Collation` property.
[get_ColorMode](#get_colormode) | Gets the `ColorMode` property.
[get_Copies](#get_copies) | Gets the `Copies` property.
[get_Duplex](#get_duplex) | Gets the `Duplex` property.
[get_MediaSize](#get_mediasize) | Gets the `MediaSize` property.
[get_PageRanges](#get_pageranges) | Gets the `PageRanges` property.
[get_PagesPerSide](#get_pagesperside) | Gets the `PagesPerSide` property.
[get_PrinterName](#get_printername) | Gets the `PrinterName` property.
[put_Collation](#put_collation) | Sets the `Collation` property.
[put_ColorMode](#put_colormode) | Sets the `ColorMode` property.
[put_Copies](#put_copies) | Sets the `Copies` property.
[put_Duplex](#put_duplex) | Sets the `Duplex` property.
[put_MediaSize](#put_mediasize) | Sets the `MediaSize` property.
[put_PageRanges](#put_pageranges) | Sets the `PageRanges` property.
[put_PagesPerSide](#put_pagesperside) | Sets the `PagesPerSide` property.
[put_PrinterName](#put_printername) | Sets the `PrinterName` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### get_Collation

Gets the `Collation` property.

> public HRESULT [get_Collation](#get_collation)(COREWEBVIEW2_PRINT_COLLATION * value)

#### get_ColorMode

Gets the `ColorMode` property.

> public HRESULT [get_ColorMode](#get_colormode)(COREWEBVIEW2_PRINT_COLOR_MODE * value)

#### get_Copies

Gets the `Copies` property.

> public HRESULT [get_Copies](#get_copies)(INT32 * value)

#### get_Duplex

Gets the `Duplex` property.

> public HRESULT [get_Duplex](#get_duplex)(COREWEBVIEW2_PRINT_DUPLEX * value)

#### get_MediaSize

Gets the `MediaSize` property.

> public HRESULT [get_MediaSize](#get_mediasize)(COREWEBVIEW2_PRINT_MEDIA_SIZE * value)

#### get_PageRanges

Gets the `PageRanges` property.

> public HRESULT [get_PageRanges](#get_pageranges)(LPWSTR * value)

#### get_PagesPerSide

Gets the `PagesPerSide` property.

> public HRESULT [get_PagesPerSide](#get_pagesperside)(INT32 * value)

#### get_PrinterName

Gets the `PrinterName` property.

> public HRESULT [get_PrinterName](#get_printername)(LPWSTR * value)

#### put_Collation

Sets the `Collation` property.

> public HRESULT [put_Collation](#put_collation)(COREWEBVIEW2_PRINT_COLLATION value)

#### put_ColorMode

Sets the `ColorMode` property.

> public HRESULT [put_ColorMode](#put_colormode)(COREWEBVIEW2_PRINT_COLOR_MODE value)

#### put_Copies

Sets the `Copies` property.

> public HRESULT [put_Copies](#put_copies)(INT32 value)

#### put_Duplex

Sets the `Duplex` property.

> public HRESULT [put_Duplex](#put_duplex)(COREWEBVIEW2_PRINT_DUPLEX value)

#### put_MediaSize

Sets the `MediaSize` property.

> public HRESULT [put_MediaSize](#put_mediasize)(COREWEBVIEW2_PRINT_MEDIA_SIZE value)

#### put_PageRanges

Sets the `PageRanges` property.

> public HRESULT [put_PageRanges](#put_pageranges)(LPCWSTR value)

#### put_PagesPerSide

Sets the `PagesPerSide` property.

> public HRESULT [put_PagesPerSide](#put_pagesperside)(INT32 value)

#### put_PrinterName

Sets the `PrinterName` property.

> public HRESULT [put_PrinterName](#put_printername)(LPCWSTR value)

