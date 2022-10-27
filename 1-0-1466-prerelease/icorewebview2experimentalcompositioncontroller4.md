---
description: This interface is an extension of the ICoreWebView2CompositionController.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCompositionController4
ms.date: 10/27/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCompositionController4
---

# interface ICoreWebView2ExperimentalCompositionController4

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCompositionController4
  : public IUnknown
```

This interface is an extension of the [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid) | A helper function to convert a pointerId received from the system into an ICoreWebView2ExperimentalPointerInfo.
[get_AutomationProvider](#get_automationprovider) | Returns the UI Automation Provider for the WebView.
[COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) | Matrix that represents a 3D transform.
[COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level) | Specifies memory usage target level of WebView.
[COREWEBVIEW2_PRINT_COLLATION](#corewebview2_print_collation) | Specifies the collation for a print.
[COREWEBVIEW2_PRINT_COLOR_MODE](#corewebview2_print_color_mode) | Specifies the color mode for a print.
[COREWEBVIEW2_PRINT_DIALOG_KIND](#corewebview2_print_dialog_kind) | Specifies the print dialog kind.
[COREWEBVIEW2_PRINT_DUPLEX](#corewebview2_print_duplex) | Specifies the duplex option for a print.
[COREWEBVIEW2_PRINT_MEDIA_SIZE](#corewebview2_print_media_size) | Specifies the media size for a print.
[COREWEBVIEW2_PRINT_STATUS](#corewebview2_print_status) | Indicates the status for printing.
[COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access) | Specifies the desired access from script to `CoreWebView2SharedBuffer`.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.
[COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds) | Specifies the source of `WebResourceRequested` event.

An object implementing ICoreWebView2ExperimentalCompositionController4 interface will also implement [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.790

## Members

#### CreateCoreWebView2PointerInfoFromPointerId

A helper function to convert a pointerId received from the system into an ICoreWebView2ExperimentalPointerInfo.

> public HRESULT [CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid)(UINT pointerId, HWND parentWindow, struct [COREWEBVIEW2_MATRIX_4X4](icorewebview2experimentalcompositioncontroller4--corewebview2_matrix_4x4.md) transform, [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) ** pointerInfo)

parentWindow is the HWND that contains the WebView. This can be any HWND in the hwnd tree that contains the WebView. The [COREWEBVIEW2_MATRIX_4X4](icorewebview2experimentalcompositioncontroller4--corewebview2_matrix_4x4.md) is the transform from that HWND to the WebView. The returned ICoreWebView2ExperimentalPointerInfo is used in SendPointerInfo. The pointer type must be either pen or touch or the function will fail.

#### get_AutomationProvider

Returns the UI Automation Provider for the WebView.

> public HRESULT [get_AutomationProvider](#get_automationprovider)(IUnknown ** provider)

#### COREWEBVIEW2_MATRIX_4X4

Matrix that represents a 3D transform.

> typedef [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4)

This transform is used to calculate correct coordinates when calling CreateCoreWebView2PointerInfoFromPointerId. This is equivalent to a D2D1_MATRIX_4X4_F

#### COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL

Specifies memory usage target level of WebView.

> enum [COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL            | Specifies normal memory usage target level.
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW            | Specifies low memory usage target level.

#### COREWEBVIEW2_PRINT_COLLATION

Specifies the collation for a print.

> enum [COREWEBVIEW2_PRINT_COLLATION](#corewebview2_print_collation)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_COLLATION_DEFAULT            | The default collation for a printer.
COREWEBVIEW2_PRINT_COLLATION_COLLATED            | Indicate that the collation has been selected for the printed output.
COREWEBVIEW2_PRINT_COLLATION_UNCOLLATED            | Indicate that the collation has not been selected for the printed output.

#### COREWEBVIEW2_PRINT_COLOR_MODE

Specifies the color mode for a print.

> enum [COREWEBVIEW2_PRINT_COLOR_MODE](#corewebview2_print_color_mode)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_COLOR_MODE_DEFAULT            | The default color mode for a printer.
COREWEBVIEW2_PRINT_COLOR_MODE_COLOR            | Indicate that the printed output will be in color.
COREWEBVIEW2_PRINT_COLOR_MODE_GRAYSCALE            | Indicate that the printed output will be in shades of gray.

#### COREWEBVIEW2_PRINT_DIALOG_KIND

Specifies the print dialog kind.

> enum [COREWEBVIEW2_PRINT_DIALOG_KIND](#corewebview2_print_dialog_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_DIALOG_KIND_BROWSER            | Opens the browser print preview dialog.
COREWEBVIEW2_PRINT_DIALOG_KIND_SYSTEM            | Opens the system print dialog.

#### COREWEBVIEW2_PRINT_DUPLEX

Specifies the duplex option for a print.

> enum [COREWEBVIEW2_PRINT_DUPLEX](#corewebview2_print_duplex)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_DUPLEX_DEFAULT            | The default duplex for a printer.
COREWEBVIEW2_PRINT_DUPLEX_ONE_SIDED            | Print on only one side of the sheet.
COREWEBVIEW2_PRINT_DUPLEX_TWO_SIDED_LONG_EDGE            | Print on both sides of the sheet, flipped along the long edge.
COREWEBVIEW2_PRINT_DUPLEX_TWO_SIDED_SHORT_EDGE            | Print on both sides of the sheet, flipped along the short edge.

#### COREWEBVIEW2_PRINT_MEDIA_SIZE

Specifies the media size for a print.

> enum [COREWEBVIEW2_PRINT_MEDIA_SIZE](#corewebview2_print_media_size)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_MEDIA_SIZE_DEFAULT            | The default media size for a printer.
COREWEBVIEW2_PRINT_MEDIA_SIZE_CUSTOM            | Indicate custom media size that is specific to the printer.

#### COREWEBVIEW2_PRINT_STATUS

Indicates the status for printing.

> enum [COREWEBVIEW2_PRINT_STATUS](#corewebview2_print_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PRINT_STATUS_SUCCEEDED            | Indicates that the print operation is succedded.
COREWEBVIEW2_PRINT_STATUS_PRINTER_UNAVAILABLE            | Indicates that the printer is not available.
COREWEBVIEW2_PRINT_STATUS_OTHER_ERROR            | Indicates that the print operation is failed.

#### COREWEBVIEW2_SHARED_BUFFER_ACCESS

Specifies the desired access from script to `CoreWebView2SharedBuffer`.

> enum [COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY            | Script from web page only has read access to the shared buffer.
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_WRITE            | Script from web page has read and write access to the shared buffer.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

Status of UpdateRuntime operation result.

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

#### COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS

Specifies the source of `WebResourceRequested` event.

> enum [COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_NONE            | 
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_DOCUMENT            | Indicates that web resource is requested from main page including dedicated workers and iframes.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SHARED_WORKER            | Indicates that web resource is requested from shared worker.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SERVICE_WORKER            | Indicates that web resource is requested from service worker.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_ALL            | Indicates that web resource is requested from any supported source.

