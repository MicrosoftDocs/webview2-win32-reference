---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 12/02/2025
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
[COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE](#corewebview2_allowed_port_range_scope) | Specifies the scope for port configuration.
[COREWEBVIEW2_RESTART_REQUESTED_PRIORITY](#corewebview2_restart_requested_priority) | Specifies the restart requested priority level.
[COREWEBVIEW2_SENSITIVITY_LABEL_KIND](#corewebview2_sensitivity_label_kind) | Specifies the kind of sensitivity label applied to web content.
[COREWEBVIEW2_SENSITIVITY_LABELS_STATE](#corewebview2_sensitivity_labels_state) | Represents the state of sensitivity label detection and processing for web content loaded in the WebView2 control.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the `ErrorReceived` event.
[COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND](#corewebview2_transport_protocol_kind) | Specifies the transport protocol for port configuration.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.

## Members

#### COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE

> enum [COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE](#corewebview2_allowed_port_range_scope)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE_DEFAULT            | Scope applies to all components.
COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE_WEB_RTC            | Applies only to WebRTC peer-to-peer connection.

Specifies the scope for port configuration.

#### COREWEBVIEW2_RESTART_REQUESTED_PRIORITY

> enum [COREWEBVIEW2_RESTART_REQUESTED_PRIORITY](#corewebview2_restart_requested_priority)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_RESTART_REQUESTED_PRIORITY_NORMAL            | Developer should remind user to restart.
COREWEBVIEW2_RESTART_REQUESTED_PRIORITY_HIGH            | Developer should prompt user to restart as soon as possible.

Specifies the restart requested priority level.

#### COREWEBVIEW2_SENSITIVITY_LABEL_KIND

> enum [COREWEBVIEW2_SENSITIVITY_LABEL_KIND](#corewebview2_sensitivity_label_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SENSITIVITY_LABEL_KIND_MIP            | Represents a Microsoft Information Protection (MIP) sensitivity label.

Specifies the kind of sensitivity label applied to web content.

Sensitivity labels are used to classify and protect content based on its sensitivity level.

This enumeration is designed to be extensible. New values may be added in future versions. Applications should not implement a default case that assumes knowledge of all possible label kinds to ensure forward compatibility.

#### COREWEBVIEW2_SENSITIVITY_LABELS_STATE

> enum [COREWEBVIEW2_SENSITIVITY_LABELS_STATE](#corewebview2_sensitivity_labels_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_SENSITIVITY_LABELS_STATE_NOT_APPLICABLE            | Indicates that none of the loaded pages are in the allow list.
COREWEBVIEW2_SENSITIVITY_LABELS_STATE_PENDING            | Indicates that WebView2 has loaded pages from the allow list that can report sensitivity labels, but the label are not available yet complete.
COREWEBVIEW2_SENSITIVITY_LABELS_STATE_AVAILABLE            | Indicates that WebView2 has loaded pages from the allow list, and the labels about the content are available now.

Represents the state of sensitivity label detection and processing for web content loaded in the WebView2 control.

#### COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND

> enum [COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND_NO_VIDEO_TRACK_STARTED            | CreateTexture/PresentTexture and so on should return failed HRESULT if the texture stream is in the stopped state rather than using the error event.
COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND_TEXTURE_ERROR            | The texture already has been removed using CloseTexture.
COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND_TEXTURE_IN_USE            | The texture to be presented is already in use for rendering.

Kinds of errors that can be reported by the `ErrorReceived` event.

#### COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND

> enum [COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND](#corewebview2_transport_protocol_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND_UDP            | User Datagram Protocol - fast, connectionless protocol.

Specifies the transport protocol for port configuration.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

Status of UpdateRuntime operation result.

