---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
topic_type: 
- APIRef
api_name:
- CreateOrJoinCoreWebView2ClusterEnvironment
- GetCoreWebView2ClusterEnvironmentOptions
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
[COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE](#corewebview2_allowed_port_range_scope) | Specifies the scope for port configuration.
[COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS](#corewebview2_cluster_environment_status) | The outcome of `CreateOrJoinCoreWebView2ClusterEnvironment`, reported to the completion handler when its `errorCode` is `S_OK`.
[COREWEBVIEW2_DIAGNOSTIC_CATEGORY](#corewebview2_diagnostic_category) | Specifies the category of diagnostic event.
[COREWEBVIEW2_DIAGNOSTIC_SCOPE](#corewebview2_diagnostic_scope) | Specifies the scope that originated a diagnostic event.
[COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE](#corewebview2_enhanced_security_mode_state) | Enhanced Security Mode state.
[COREWEBVIEW2_ORIGIN_FEATURE](#corewebview2_origin_feature) | Specifies the feature types that can be configured for origins.
[COREWEBVIEW2_ORIGIN_FEATURE_STATE](#corewebview2_origin_feature_state) | Specifies the state of an origin feature.
[COREWEBVIEW2_RESTART_REQUESTED_PRIORITY](#corewebview2_restart_requested_priority) | Specifies the restart requested priority level.
[COREWEBVIEW2_SENSITIVITY_LABEL_KIND](#corewebview2_sensitivity_label_kind) | Specifies the kind of sensitivity label applied to web content.
[COREWEBVIEW2_SENSITIVITY_LABELS_STATE](#corewebview2_sensitivity_labels_state) | Represents the state of sensitivity label detection and processing for web content loaded in the WebView2 control.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the `ErrorReceived` event.
[COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND](#corewebview2_transport_protocol_kind) | Specifies the transport protocol for port configuration.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.
[CreateOrJoinCoreWebView2ClusterEnvironment](#createorjoincorewebview2clusterenvironment) | Establishes, or attaches to, a shared WebView2 cluster environment identified by the `ClusterName` in `options`.
[GetCoreWebView2ClusterEnvironmentOptions](#getcorewebview2clusterenvironmentoptions) | Synchronously reads the options of the cluster currently running for `clusterName`, without spawning a browser.

## Members

#### COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE

> enum [COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE](#corewebview2_allowed_port_range_scope)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE_DEFAULT            | Scope applies to all components.
COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE_WEB_RTC            | Applies only to WebRTC peer-to-peer connection.

Specifies the scope for port configuration.

#### COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS

> enum [COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS](#corewebview2_cluster_environment_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS_SUCCEEDED            | The shared cluster environment is ready, either freshly established or attached to an existing cluster with matching options.
COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS_OPTIONS_MISMATCH            | A cluster already exists for this `ClusterName` with different options.
COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS_NOT_SUPPORTED            | This host cannot use cluster environments, for example a sandboxed AppContainer process such as a UWP app.

The outcome of `CreateOrJoinCoreWebView2ClusterEnvironment`, reported to the completion handler when its `errorCode` is `S_OK`.

#### COREWEBVIEW2_DIAGNOSTIC_CATEGORY

> enum [COREWEBVIEW2_DIAGNOSTIC_CATEGORY](#corewebview2_diagnostic_category)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DIAGNOSTIC_CATEGORY_NETWORK_REQUEST            | Network request lifecycle signal.

Specifies the category of diagnostic event.

Each value defines its own JSON schemas for the filter accepted by `ICoreWebView2DiagnosticMonitor::SetDiagnosticFilter` and for the details returned by `ICoreWebView2DiagnosticReceivedEventArgs::DetailsAsJson`.

#### COREWEBVIEW2_DIAGNOSTIC_SCOPE

> enum [COREWEBVIEW2_DIAGNOSTIC_SCOPE](#corewebview2_diagnostic_scope)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_DIAGNOSTIC_SCOPE_WEBVIEW            | The diagnostic signal originated from a specific WebView instance.
COREWEBVIEW2_DIAGNOSTIC_SCOPE_PROFILE            | The diagnostic signal originated from a profile but is not tied to a specific WebView.
COREWEBVIEW2_DIAGNOSTIC_SCOPE_ENVIRONMENT            | The diagnostic signal originated from the environment (for example, a browser-wide event that affects all WebViews).

Specifies the scope that originated a diagnostic event.

#### COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE

> enum [COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE](#corewebview2_enhanced_security_mode_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE_DISABLED            | Enhanced Security Mode is disabled.
COREWEBVIEW2_ENHANCED_SECURITY_MODE_STATE_ENABLED            | Enhanced Security Mode is enabled.

Enhanced Security Mode state.

#### COREWEBVIEW2_ORIGIN_FEATURE

> enum [COREWEBVIEW2_ORIGIN_FEATURE](#corewebview2_origin_feature)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_ORIGIN_FEATURE_ENHANCED_SECURITY_MODE            | Specifies enhanced security mode settings for the origin.
COREWEBVIEW2_ORIGIN_FEATURE_REPUTATION_CHECKING            | Specifies per-origin reputation checking settings.

Specifies the feature types that can be configured for origins.

#### COREWEBVIEW2_ORIGIN_FEATURE_STATE

> enum [COREWEBVIEW2_ORIGIN_FEATURE_STATE](#corewebview2_origin_feature_state)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_ORIGIN_FEATURE_STATE_ENABLED            | Sets the enabled state of the origin feature.
COREWEBVIEW2_ORIGIN_FEATURE_STATE_DISABLED            | Sets the disabled state of the origin feature.

Specifies the state of an origin feature.

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

#### CreateOrJoinCoreWebView2ClusterEnvironment

> public STDAPI [CreateOrJoinCoreWebView2ClusterEnvironment](#createorjoincorewebview2clusterenvironment)([ICoreWebView2ExperimentalClusterEnvironmentOptions](icorewebview2experimentalclusterenvironmentoptions.md#icorewebview2experimentalclusterenvironmentoptions) * options, [ICoreWebView2ExperimentalCreateOrJoinClusterEnvironmentCompletedHandler](icorewebview2experimentalcreateorjoinclusterenvironmentcompletedhandler.md#icorewebview2experimentalcreateorjoinclusterenvironmentcompletedhandler) * handler)

Establishes, or attaches to, a shared WebView2 cluster environment identified by the `ClusterName` in `options`.

This is the symmetric entry point every cooperating host calls with its full desired options.

A cluster exists only while its browser process is running. The first host to establish a cluster for a given `ClusterName` (when no browser is running for it) pins its options and cold-starts the shared browser. While that browser is alive, a later host attaches when its options equal the pinned set (strict, full-set equality) and the completion handler receives the shared [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment). A host whose options differ from the live pinned set does not attach: the completion handler reports `COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS_OPTIONS_MISMATCH` with a null environment; that host should call `GetCoreWebView2ClusterEnvironmentOptions` to read the authoritative set and retry, or create a private (non-shared) environment instead. Once the cluster's browser exits the pinned set no longer applies, so the next host to call this method becomes the new first creator and may pin a different set.

A host that cannot use cluster environments, such as a sandboxed AppContainer process, is not a failure of the call: the operation starts and the completion handler reports `COREWEBVIEW2_CLUSTER_ENVIRONMENT_STATUS_NOT_SUPPORTED` with a null environment. That host should create a private environment instead.

The mapping from `ClusterName` to the on-disk user data folder is a fixed function, so the same `ClusterName` always resolves to the same layout.

The threading requirements match `CreateCoreWebView2EnvironmentWithOptions`: the app must have run `CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED)` first, and `handler` is invoked on the calling thread, which must pump a message loop for the handler to run.

#### GetCoreWebView2ClusterEnvironmentOptions

> public STDAPI [GetCoreWebView2ClusterEnvironmentOptions](#getcorewebview2clusterenvironmentoptions)(PCWSTR clusterName, [ICoreWebView2ExperimentalClusterEnvironmentOptions](icorewebview2experimentalclusterenvironmentoptions.md#icorewebview2experimentalclusterenvironmentoptions) ** options)

Synchronously reads the options of the cluster currently running for `clusterName`, without spawning a browser.

Use this to pre-flight before calling `CreateOrJoinCoreWebView2ClusterEnvironment`: read what the live cluster is using and decide whether to reuse it or offer your own set.

Returns `S_OK` and the pinned options when a cluster is currently running for `clusterName`. Returns `S_OK` and null `options` when no cluster is running for `clusterName` (whether it was never created or its browser has since exited); the on-disk pinned record of a cluster whose browser has exited is stale and is not returned. No cluster is an expected result, so check `options` for null rather than for a failing `HRESULT`. Also returns `S_OK` and null `options` in a host that cannot use cluster environments, such as a sandboxed AppContainer process.

The value returned is a hint: it can be stale the instant it is read if the cluster's browser exits or another host establishes a different set concurrently. `CreateOrJoinCoreWebView2ClusterEnvironment` remains authoritative and validates against the live cluster.

