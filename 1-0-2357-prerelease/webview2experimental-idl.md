---
description: WebView2 Win32 Experimental Globals
title: Experimental Globals
ms.date: 02/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html
topic_type: 
- APIRef
api_name:
- GetAvailableCoreWebView2BrowserVersionStringWithOptions
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
[COREWEBVIEW2_CHANNEL_SEARCH_KIND](#corewebview2_channel_search_kind) | The channel search kind determines the order that release channels are searched for during environment creation.
[COREWEBVIEW2_NON_CLIENT_REGION_KIND](#corewebview2_non_client_region_kind) | This enum contains values representing possible regions a given point lies within.
[COREWEBVIEW2_RELEASE_CHANNELS](#corewebview2_release_channels) | The WebView2 release channels.
[COREWEBVIEW2_TEXT_DIRECTION_KIND](#corewebview2_text_direction_kind) | Indicates the text direction of the notification.
[COREWEBVIEW2_TEXTURE_STREAM_ERROR_KIND](#corewebview2_texture_stream_error_kind) | Kinds of errors that can be reported by the ICoreWebView2ExperimentalTextureStream ErrorReceived event.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.
[GetAvailableCoreWebView2BrowserVersionStringWithOptions](#getavailablecorewebview2browserversionstringwithoptions) | This function will tell you the browser version info of the release channel used when creating an environment with the same options.

## Members

#### COREWEBVIEW2_CHANNEL_SEARCH_KIND

> enum [COREWEBVIEW2_CHANNEL_SEARCH_KIND](#corewebview2_channel_search_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE            | Search for a release channel from most to least stable: WebView2 Runtime -> Beta -> Dev -> Canary.
COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE            | Search for a release channel from least to most stable: Canary -> Dev -> Beta -> WebView2 Runtime.

The channel search kind determines the order that release channels are searched for during environment creation.

The default behavior is to search for and use the most stable channel found on the device. The order from most to least stable is: WebView2 Runtime -> Beta -> Dev -> Canary. Switch the order to prefer the least stable channel in order to perform pre-release testing. See `COREWEBVIEW2_RELEASE_CHANNELS` for descriptions of channels.

#### COREWEBVIEW2_NON_CLIENT_REGION_KIND

> enum [COREWEBVIEW2_NON_CLIENT_REGION_KIND](#corewebview2_non_client_region_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_NON_CLIENT_REGION_KIND_NOWHERE            | A hit test region out of bounds of the WebView2.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_CLIENT            | A hit test region in the WebView2 which does not have the CSS style `-webkit-app-region: drag` set.
COREWEBVIEW2_NON_CLIENT_REGION_KIND_CAPTION            | A hit test region in the WebView2 which has the CSS style `-webkit-app-region: drag` set.

This enum contains values representing possible regions a given point lies within.

#### COREWEBVIEW2_RELEASE_CHANNELS

> enum [COREWEBVIEW2_RELEASE_CHANNELS](#corewebview2_release_channels)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_RELEASE_CHANNELS_NONE            | No release channel.
COREWEBVIEW2_RELEASE_CHANNELS_STABLE            | The stable WebView2 Runtime that is released every 4 weeks.
COREWEBVIEW2_RELEASE_CHANNELS_BETA            | The Beta release channel that is released every 4 weeks, a week before the stable release.
COREWEBVIEW2_RELEASE_CHANNELS_DEV            | The Dev release channel that is released weekly.
COREWEBVIEW2_RELEASE_CHANNELS_CANARY            | The Canary release channel that is released daily.

The WebView2 release channels.

Use `ReleaseChannels` and `ChannelSearchKind` on ICoreWebView2EnvironmentOptions to control which channel is searched for during environment creation. 
Channel   |Primary purpose   |How often updated with new features
--------- | --------- | ---------
Stable (WebView2 Runtime)   |Broad Deployment   |Monthly
Beta   |Flighting with inner rings, automated testing   |Monthly
Dev   |Automated testing, selfhosting to test new APIs and features   |Weekly
Canary   |Automated testing, selfhosting to test new APIs and features   |Daily

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

#### GetAvailableCoreWebView2BrowserVersionStringWithOptions

> public STDAPI [GetAvailableCoreWebView2BrowserVersionStringWithOptions](#getavailablecorewebview2browserversionstringwithoptions)(PCWSTR browserExecutableFolder, ICoreWebView2EnvironmentOptions * environmentOptions, LPWSTR * versionInfo)

This function will tell you the browser version info of the release channel used when creating an environment with the same options.

Browser version info includes channel name if it is not the WebView2 Runtime. Channel names are Beta, Dev, and Canary. The format of the return string matches the format of `BrowserVersionString` on ICoreWebView2Environment.

If an override exists for `browserExecutableFolder`, `releaseChannels`, or `ChannelSearchKind`, the override is used. The presence of an override can result in a different channel used than the one expected based on the environment options object. `browserExecutableFolder` takes precedence over the other options, regardless of whether or not its channel is included in the `releaseChannels`. See `CreateCoreWebView2EnvironmentWithOptions` for more details on overrides. If an override is not specified, then the parameters passed to `GetAvailableCoreWebView2BrowserVersionStringWithOptions` are used. Returns `HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)` if it fails to find an installed WebView2 Runtime or non-stable Microsoft Edge installation. Use `GetAvailableCoreWebView2BrowserVersionString` to get the version info without the environment options.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

