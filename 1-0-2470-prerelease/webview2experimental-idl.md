---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 03/25/2024
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

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND](#corewebview2_file_system_handle_kind) | Kind of CoreWebView2FileSystemHandle as described in [FileSystemHandle.kind](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/kind)
[COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION](#corewebview2_file_system_handle_permission) | Allowed permissions of a CoreWebView2FileSystemHandle as described in [FileSystemHandle.requestPermission()](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/requestPermission)
[COREWEBVIEW2_SCROLLBAR_STYLE](#corewebview2_scrollbar_style) | Set ScrollBar style on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) during environment creation.
[COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind) | Indicates the text direction of the notification.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the [ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) ErrorReceived event.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.

## Members

#### COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND

> enum [COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND](#corewebview2_file_system_handle_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND_FILE            | FileSystemHandle is for a file (i.e.
COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND_DIRECTORY            | FileSystemHandle is for a directory (i.e.

Kind of CoreWebView2FileSystemHandle as described in [FileSystemHandle.kind](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/kind)

#### COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION

> enum [COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION](#corewebview2_file_system_handle_permission)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_ONLY            | Read-only permission for FileSystemHandle.
COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION_READ_WRITE            | Read and write permissions for FileSystemHandle.

Allowed permissions of a CoreWebView2FileSystemHandle as described in [FileSystemHandle.requestPermission()](https://developer.mozilla.org/docs/Web/API/FileSystemHandle/requestPermission)

#### COREWEBVIEW2_SCROLLBAR_STYLE

> enum [COREWEBVIEW2_SCROLLBAR_STYLE](#corewebview2_scrollbar_style)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SCROLLBAR_STYLE_DEFAULT            | Browser default ScrollBar style.
COREWEBVIEW2_SCROLLBAR_STYLE_FLUENT_OVERLAY            | Window style fluent overlay scroll bar Please see [Fluent UI](https://developer.microsoft.com/en-us/fluentui#/) for more details on fluent UI.

Set ScrollBar style on [ICoreWebView2EnvironmentOptions](icorewebview2environmentoptions.md#icorewebview2environmentoptions) during environment creation.

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

Kinds of errors that can be reported by the [ICoreWebView2ExperimentalTextureStream](icorewebview2experimentaltexturestream.md#icorewebview2experimentaltexturestream) ErrorReceived event.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

Status of UpdateRuntime operation result.

