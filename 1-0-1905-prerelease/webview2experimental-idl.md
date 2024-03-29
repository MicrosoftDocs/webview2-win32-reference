---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 07/24/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
---

# Experimental Globals

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) | Matrix that represents a 3D transform.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the ICoreWebView2ExperimentalTextureStream ErrorReceived event.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.
[COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds) | Specifies the source of `WebResourceRequested` event.

## Members

#### COREWEBVIEW2_MATRIX_4X4

Matrix that represents a 3D transform.

> typedef [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4)
This transform is used to calculate correct coordinates when calling CreateCoreWebView2PointerInfoFromPointerId. This is equivalent to a D2D1_MATRIX_4X4_F

#### COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND

> enum [COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TEXTURE_STREAM_ERROR_NO_VIDEO_TRACK_STARTED            | CreateTexture/PresentTexture and so on should return failed HRESULT if the texture stream is in the stopped state rather than using the error event.
COREWEBVIEW2_TEXTURE_STREAM_ERROR_TEXTURE_ERROR            | The texture already has been removed using CloseTexture.
COREWEBVIEW2_TEXTURE_STREAM_ERROR_TEXTURE_IN_USE            | The texture to be presented is already in use for rendering.

Kinds of errors that can be reported by the ICoreWebView2ExperimentalTextureStream ErrorReceived event.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

Status of UpdateRuntime operation result.

#### COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS

> enum [COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_NONE            | 
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_DOCUMENT            | Indicates that web resource is requested from main page including dedicated workers and iframes.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SHARED_WORKER            | Indicates that web resource is requested from shared worker.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SERVICE_WORKER            | Indicates that web resource is requested from service worker.
COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_ALL            | Indicates that web resource is requested from any supported source.

Specifies the source of `WebResourceRequested` event.

