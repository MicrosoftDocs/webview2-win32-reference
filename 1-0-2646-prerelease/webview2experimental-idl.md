---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 07/31/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
topic_type: 
- APIRef
api_name:
api_type:
- DllExport
api_location:
- WebView2Loader.dll
---

# Experimental Globals

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_SAVE_AS_KIND](#corewebview2_save_as_kind) | Specifies Save As kind selection options for `ICoreWebView2SaveAsUIShowingEventArgs`.
[COREWEBVIEW2_SAVE_AS_UI_RESULT](#corewebview2_save_as_ui_result) | Status of a programmatic Save As call.
[COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind) | Indicates the text direction of the notification.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the `ErrorReceived` event.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.

## Members

#### COREWEBVIEW2_SAVE_AS_KIND

> enum [COREWEBVIEW2_SAVE_AS_KIND](#corewebview2_save_as_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SAVE_AS_KIND_DEFAULT            | Default kind to save non-HTML content.
COREWEBVIEW2_SAVE_AS_KIND_HTML_ONLY            | Save the page as HTML.
COREWEBVIEW2_SAVE_AS_KIND_SINGLE_FILE            | Save the page as [MHTML](https://en.wikipedia.org/wiki/MHTML).
COREWEBVIEW2_SAVE_AS_KIND_COMPLETE            | Save the page as HTML and download the page-related source files (for example: CSS, JavaScript, images, etc.) in a directory with the same filename prefix.

Specifies Save As kind selection options for `ICoreWebView2SaveAsUIShowingEventArgs`.

For HTML documents, we support 3 Save As kinds: HTML_ONLY, SINGLE_FILE and COMPLETE. For non-HTML documents, you must use DEFAULT. MIME types of `text/html` and `application/xhtml+xml` are considered HTML documents.

#### COREWEBVIEW2_SAVE_AS_UI_RESULT

> enum [COREWEBVIEW2_SAVE_AS_UI_RESULT](#corewebview2_save_as_ui_result)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SAVE_AS_UI_RESULT_SUCCESS            | The ShowSaveAsUI method call completed successfully.
COREWEBVIEW2_SAVE_AS_UI_RESULT_INVALID_PATH            | Could not perform Save As because the destination file path is an invalid path.
COREWEBVIEW2_SAVE_AS_UI_RESULT_FILE_ALREADY_EXISTS            | Could not perform Save As because the destination file path already exists and replacing files was not allowed by the `AllowReplace` property.
COREWEBVIEW2_SAVE_AS_UI_RESULT_KIND_NOT_SUPPORTED            | Could not perform Save As because the `Kind` property selection is not supported due to content MIME type or system limits.
COREWEBVIEW2_SAVE_AS_UI_RESULT_CANCELLED            | Did not perform Save As because the end user cancelled or the `Cancel` property on `ICoreWebView2SaveAsUIShowingEventArgs` was set to TRUE.

Status of a programmatic Save As call.

Indicates the result of the `ShowSaveAsUI` method.

#### COREWEBVIEW2_MATRIX_4X4

Matrix that represents a 3D transform.

> typedef [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4)
This transform is used to calculate correct coordinates when calling CreateCoreWebView2PointerInfoFromPointerId. This is equivalent to a D2D1_MATRIX_4X4_F

#### COREWEBVIEW2_TEXT_DIRECTION_KIND

> enum [COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TEXT_DIRECTION_KIND_DEFAULT            | Indicates that the notification text direction adopts the browser's language setting behavior.
COREWEBVIEW2_TEXT_DIRECTION_KIND_LEFT_TO_RIGHT            | Indicates that the notification text is left-to-right.
COREWEBVIEW2_TEXT_DIRECTION_KIND_RIGHT_TO_LEFT            | Indicates that the notification text is right-to-left.

Indicates the text direction of the notification.

#### COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND

> enum [COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND_NO_VIDEO_TRACK_STARTED            | CreateTexture/PresentTexture and so on should return failed HRESULT if the texture stream is in the stopped state rather than using the error event.
COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND_TEXTURE_ERROR            | The texture already has been removed using CloseTexture.
COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND_TEXTURE_IN_USE            | The texture to be presented is already in use for rendering.

Kinds of errors that can be reported by the `ErrorReceived` event.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

Status of UpdateRuntime operation result.

