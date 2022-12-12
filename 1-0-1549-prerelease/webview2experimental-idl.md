---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 12/13/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
---

# Experimental Globals

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) | Matrix that represents a 3D transform.
[COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level) | Specifies memory usage target level of WebView.
[COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access) | Specifies the desired access from script to `CoreWebView2SharedBuffer`.
[COREWEBVIEW2_TRACKING_PREVENTION_LEVEL](#corewebview2_tracking_prevention_level) | Tracking prevention levels.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.
[COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](#corewebview2_web_resource_request_source_kinds) | Specifies the source of `WebResourceRequested` event.

## Members

#### COREWEBVIEW2_MATRIX_4X4 

Matrix that represents a 3D transform.

> typedef [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4)

This transform is used to calculate correct coordinates when calling CreateCoreWebView2PointerInfoFromPointerId. This is equivalent to a D2D1_MATRIX_4X4_F.

#### COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL

> enum [COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_NORMAL            | Specifies normal memory usage target level.
COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL_LOW            | Specifies low memory usage target level.

Specifies memory usage target level of WebView.

#### COREWEBVIEW2_SHARED_BUFFER_ACCESS

> enum [COREWEBVIEW2_SHARED_BUFFER_ACCESS](#corewebview2_shared_buffer_access)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_ONLY            | Script from web page only has read access to the shared buffer.
COREWEBVIEW2_SHARED_BUFFER_ACCESS_READ_WRITE            | Script from web page has read and write access to the shared buffer.

Specifies the desired access from script to `CoreWebView2SharedBuffer`.

#### COREWEBVIEW2_TRACKING_PREVENTION_LEVEL

> enum [COREWEBVIEW2_TRACKING_PREVENTION_LEVEL](#corewebview2_tracking_prevention_level)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_NONE            | Tracking prevention is turned off.
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BASIC            | The least restrictive level of tracking prevention.
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BALANCED            | The default level of tracking prevention.
COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_STRICT            | The most restrictive level of tracking prevention.

Tracking prevention levels.

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

