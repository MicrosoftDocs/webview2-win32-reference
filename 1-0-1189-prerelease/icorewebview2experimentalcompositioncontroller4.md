---
description: This interface is an extension of the ICoreWebView2CompositionController.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCompositionController4
ms.date: 04/12/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCompositionController4
---

# interface ICoreWebView2ExperimentalCompositionController4

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

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
[COREWEBVIEW2_BROWSING_DATA_KINDS](#corewebview2_browsing_data_kinds) | Specifies the datatype for the [ICoreWebView2ExperimentalProfile4::ClearBrowsingData](icorewebview2experimentalprofile4.md) method.
[COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) | Matrix that represents a 3D transform.
[COREWEBVIEW2_MEMORY_USAGE_TARGET_LEVEL](#corewebview2_memory_usage_target_level) | Specifies memory usage target level of WebView.
[COREWEBVIEW2_PREFERRED_COLOR_SCHEME](#corewebview2_preferred_color_scheme) | An enum to represent the options for WebView2 color scheme: auto, light, or dark.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.

An object implementing ICoreWebView2ExperimentalCompositionController4 interface will also implement [ICoreWebView2CompositionController](icorewebview2compositioncontroller.md).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.790

## Members

#### CreateCoreWebView2PointerInfoFromPointerId

A helper function to convert a pointerId received from the system into an ICoreWebView2ExperimentalPointerInfo.

> public HRESULT [CreateCoreWebView2PointerInfoFromPointerId](#createcorewebview2pointerinfofrompointerid)(UINT pointerId, HWND parentWindow, struct [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) transform, [ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) ** pointerInfo)

parentWindow is the HWND that contains the WebView. This can be any HWND in the hwnd tree that contains the WebView. The [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) is the transform from that HWND to the WebView. The returned ICoreWebView2ExperimentalPointerInfo is used in SendPointerInfo. The pointer type must be either pen or touch or the function will fail.

#### get_AutomationProvider

Returns the UI Automation Provider for the WebView.

> public HRESULT [get_AutomationProvider](#get_automationprovider)(IUnknown ** provider)

#### COREWEBVIEW2_BROWSING_DATA_KINDS

Specifies the datatype for the [ICoreWebView2ExperimentalProfile4::ClearBrowsingData](icorewebview2experimentalprofile4.md) method.

> enum [COREWEBVIEW2_BROWSING_DATA_KINDS](#corewebview2_browsing_data_kinds)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSING_DATA_KINDS_FILE_SYSTEMS            | Specifies file systems data.
COREWEBVIEW2_BROWSING_DATA_KINDS_INDEXED_DB            | Specifies data stored by the IndexedDB DOM feature.
COREWEBVIEW2_BROWSING_DATA_KINDS_LOCAL_STORAGE            | Specifies data stored by the localStorage DOM API.
COREWEBVIEW2_BROWSING_DATA_KINDS_WEB_SQL            | Specifies data stored by the Web SQL database DOM API.
COREWEBVIEW2_BROWSING_DATA_KINDS_CACHE_STORAGE            | Specifies data stored by the CacheStorage DOM API.
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_DOM_STORAGE            | Specifies DOM storage data, now and future.
COREWEBVIEW2_BROWSING_DATA_KINDS_COOKIES            | Specifies HTTP cookies data.
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_SITE            | Specifies all site data, now and future.
COREWEBVIEW2_BROWSING_DATA_KINDS_DISK_CACHE            | Specifies disk cache.
COREWEBVIEW2_BROWSING_DATA_KINDS_DOWNLOAD_HISTORY            | Specifies download history data.
COREWEBVIEW2_BROWSING_DATA_KINDS_GENERAL_AUTOFILL            | Specifies general autofill form data.
COREWEBVIEW2_BROWSING_DATA_KINDS_PASSWORD_AUTOSAVE            | Specifies password autosave data.
COREWEBVIEW2_BROWSING_DATA_KINDS_BROWSING_HISTORY            | Specifies browsing history data.
COREWEBVIEW2_BROWSING_DATA_KINDS_SETTINGS            | Specifies settings data.
COREWEBVIEW2_BROWSING_DATA_KINDS_ALL_PROFILE            | Specifies profile data that should be wiped to make it look like a new profile.

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

#### COREWEBVIEW2_PREFERRED_COLOR_SCHEME

An enum to represent the options for WebView2 color scheme: auto, light, or dark.

> enum [COREWEBVIEW2_PREFERRED_COLOR_SCHEME](#corewebview2_preferred_color_scheme)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_AUTO            | Auto color scheme.
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_LIGHT            | Light color scheme.
COREWEBVIEW2_PREFERRED_COLOR_SCHEME_DARK            | Dark color scheme.

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

Status of UpdateRuntime operation result.

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

