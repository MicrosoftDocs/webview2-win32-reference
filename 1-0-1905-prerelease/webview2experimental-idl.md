---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 07/20/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
topic_type: 
- APIRef
api_name:
api_type:
[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]
api_type:
- DllExport
api_location:
- WebView2Loader.dll
---

# Experimental Globals

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_FRAME_KIND](#corewebview2_frame_kind) | Indicates the frame type used in the ICoreWebView2ExperimentalFrameInfo interface.
[COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind) | Indicates the text direction of the notification.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the ICoreWebView2ExperimentalTextureStream ErrorReceived event.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.
[COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds) | Specifies the source of `WebResourceRequested` event.

## Members

#### COREWEBVIEW2_FRAME_KIND

> enum [COREWEBVIEW2_FRAME_KIND](#corewebview2_frame_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_FRAME_KIND_OTHER            | Indicates that the frame is type of frame we don't differentiate.
COREWEBVIEW2_FRAME_KIND_MAIN_FRAME            | Indicates that the frame is a primary main frame(webview).
COREWEBVIEW2_FRAME_KIND_IFRAME            | Indicates that the frame is an iframe.

Indicates the frame type used in the ICoreWebView2ExperimentalFrameInfo interface.

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

