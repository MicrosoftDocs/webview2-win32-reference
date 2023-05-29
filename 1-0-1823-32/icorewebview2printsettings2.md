---
description: Settings used by the `Print` method.
title: WebView2 Win32 C++ ICoreWebView2PrintSettings2
ms.date: 05/29/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PrintSettings2
---

# interface ICoreWebView2PrintSettings2

```
interface ICoreWebView2PrintSettings2
  : public ICoreWebView2PrintSettings
```

Settings used by the `Print` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Collation](#get_collation) | Printer collation.
[get_ColorMode](#get_colormode) | Printer color mode.
[get_Copies](#get_copies) | Number of copies to print.
[get_Duplex](#get_duplex) | Printer duplex settings.
[get_MediaSize](#get_mediasize) | Printer media size.
[get_PageRanges](#get_pageranges) | Page range to print.
[get_PagesPerSide](#get_pagesperside) | Prints multiple pages of a document on a single piece of paper.
[get_PrinterName](#get_printername) | The name of the printer to use.
[put_Collation](#put_collation) | Set the `Collation` property.
[put_ColorMode](#put_colormode) | Set the `ColorMode` property.
[put_Copies](#put_copies) | Set the `Copies` property.
[put_Duplex](#put_duplex) | Set the `Duplex` property.
[put_MediaSize](#put_mediasize) | Set the `MediaSize` property.
[put_PageRanges](#put_pageranges) | Set the `PageRanges` property.
[put_PagesPerSide](#put_pagesperside) | Set the `PagesPerSide` property.
[put_PrinterName](#put_printername) | Set the `PrinterName` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### get_Collation

Printer collation.

> public HRESULT [get_Collation](#get_collation)(COREWEBVIEW2_PRINT_COLLATION * value)

See `COREWEBVIEW2_PRINT_COLLATION` for descriptions of collation. The default value is `COREWEBVIEW2_PRINT_COLLATION_DEFAULT`.

Printing uses default value of printer's collation if an invalid value is provided for the specific printer.

This value is ignored in PrintToPdfStream method.

#### get_ColorMode

Printer color mode.

> public HRESULT [get_ColorMode](#get_colormode)(COREWEBVIEW2_PRINT_COLOR_MODE * value)

See `COREWEBVIEW2_PRINT_COLOR_MODE` for descriptions of color modes. The default value is `COREWEBVIEW2_PRINT_COLOR_MODE_DEFAULT`.

Printing uses default value of printer supported color if an invalid value is provided for the specific printer.

#### get_Copies

Number of copies to print.

> public HRESULT [get_Copies](#get_copies)(INT32 * value)

Minimum value is `1` and the maximum copies count is `999`. The default value is 1.

This value is ignored in PrintToPdfStream method.

#### get_Duplex

Printer duplex settings.

> public HRESULT [get_Duplex](#get_duplex)(COREWEBVIEW2_PRINT_DUPLEX * value)

See `COREWEBVIEW2_PRINT_DUPLEX` for descriptions of duplex. The default value is `COREWEBVIEW2_PRINT_DUPLEX_DEFAULT`.

Printing uses default value of printer's duplex if an invalid value is provided for the specific printer.

This value is ignored in PrintToPdfStream method.

#### get_MediaSize

Printer media size.

> public HRESULT [get_MediaSize](#get_mediasize)(COREWEBVIEW2_PRINT_MEDIA_SIZE * value)

See `COREWEBVIEW2_PRINT_MEDIA_SIZE` for descriptions of media size. The default value is `COREWEBVIEW2_PRINT_MEDIA_SIZE_DEFAULT`.

If media size is `COREWEBVIEW2_PRINT_MEDIA_SIZE_CUSTOM`, you should set the `PageWidth` and `PageHeight`.

Printing uses default value of printer supported media size if an invalid value is provided for the specific printer.

This value is ignored in PrintToPdfStream method.

#### get_PageRanges

Page range to print.

> public HRESULT [get_PageRanges](#get_pageranges)(LPWSTR * value)

Defaults to empty string, which means print all pages. If the Page range is empty string or null, then it applies the default.

The PageRanges property is a list of page ranges specifying one or more pages that should be printed separated by commas. Any whitespace between page ranges is ignored. A valid page range is either a single integer identifying the page to print, or a range in the form `[start page]-[last page]` where `start page` and `last page` are integers identifying the first and last inclusive pages respectively to print. Every page identifier is an integer greater than 0 unless wildcards are used (see below examples). The first page is 1.

In a page range of the form `[start page]-[last page]` the start page number must be larger than 0 and less than or equal to the document's total page count. If the `start page` is not present, then 1 is used as the `start page`. The `last page` must be larger than the `start page`. If the `last page` is not present, then the document total page count is used as the `last page`.

Repeating a page does not print it multiple times. To print multiple times, use the `Copies` property.

The pages are always printed in ascending order, even if specified in non-ascending order.

If page range is not valid or if a page is greater than document total page count, ICoreWebView2PrintCompletedHandler or ICoreWebView2PrintToPdfStreamCompletedHandler handler will return `E_INVALIDARG`.

The following examples assume a document with 20 total pages.

Example   |Result   |Notes
--------- | --------- | ---------
"2"   |Page 2   |
"1-4, 9, 3-6, 10, 11"   |Pages 1-6, 9-11   |
"1-4, -6"   |Pages 1-6   |The "-6" is interpreted as "1-6".
"2-"   |Pages 2-20   |The "2-" is interpreted as "pages 2 to the end of the document".
"4-2, 11, -6"   |Invalid   |"4-2" is an invalid range.
"-"   |Pages 1-20   |The "-" is interpreted as "page 1 to the end of the document".
"1-4dsf, 11"   |Invalid   |
"2-2"   |Page 2   |

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings)

#### get_PagesPerSide

Prints multiple pages of a document on a single piece of paper.

> public HRESULT [get_PagesPerSide](#get_pagesperside)(INT32 * value)

Choose from 1, 2, 4, 6, 9 or 16. The default value is 1.

#### get_PrinterName

The name of the printer to use.

> public HRESULT [get_PrinterName](#get_printername)(LPWSTR * value)

Defaults to empty string. If the printer name is empty string or null, then it prints to the default printer on the user OS.

This value is ignored in PrintToPdfStream method.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings)

#### put_Collation

Set the `Collation` property.

> public HRESULT [put_Collation](#put_collation)(COREWEBVIEW2_PRINT_COLLATION value)

#### put_ColorMode

Set the `ColorMode` property.

> public HRESULT [put_ColorMode](#put_colormode)(COREWEBVIEW2_PRINT_COLOR_MODE value)

#### put_Copies

Set the `Copies` property.

> public HRESULT [put_Copies](#put_copies)(INT32 value)

Returns `E_INVALIDARG` if an invalid value is provided and the current value is not changed.

#### put_Duplex

Set the `Duplex` property.

> public HRESULT [put_Duplex](#put_duplex)(COREWEBVIEW2_PRINT_DUPLEX value)

#### put_MediaSize

Set the `MediaSize` property.

> public HRESULT [put_MediaSize](#put_mediasize)(COREWEBVIEW2_PRINT_MEDIA_SIZE value)

#### put_PageRanges

Set the `PageRanges` property.

> public HRESULT [put_PageRanges](#put_pageranges)(LPCWSTR value)

#### put_PagesPerSide

Set the `PagesPerSide` property.

> public HRESULT [put_PagesPerSide](#put_pagesperside)(INT32 value)

Returns `E_INVALIDARG` if an invalid value is provided, and the current value is not changed.

Below examples shows print output for PagesPerSide and Duplex.

PagesPerSide   |Total pages   |Two-sided printing   |Result
--------- | --------- | --------- | ---------
1   |1   |-   |1 page on the front side.
2   |1   |Yes   |1 page on the front side.
2   |4   |-   |2 pages on the first paper and 2 pages on the next paper.
2   |4   |Yes   |2 pages on the front side and 2 pages on back side.
4   |4   |Yes   |4 pages on the front side.
4   |8   |Yes   |4 pages on the front side and 4 pages on the back side.

#### put_PrinterName

Set the `PrinterName` property.

> public HRESULT [put_PrinterName](#put_printername)(LPCWSTR value)

If provided printer name doesn't match with the name of any installed printers on the user OS, ICoreWebView2PrintCompletedHandler handler will return `errorCode` as `S_OK` and `printStatus` as COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE.

Use [Enum Printers](/windows/win32/printdocs/enumprinters) to enumerate available printers.

