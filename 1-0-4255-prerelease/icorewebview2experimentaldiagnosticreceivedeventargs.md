---
description: Event args for the `DiagnosticReceived` event on ICoreWebView2ExperimentalDiagnosticMonitor.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDiagnosticReceivedEventArgs
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDiagnosticReceivedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDiagnosticReceivedEventArgs
- ICoreWebView2ExperimentalDiagnosticReceivedEventArgs.get_Category
- ICoreWebView2ExperimentalDiagnosticReceivedEventArgs.get_DetailsAsJson
- ICoreWebView2ExperimentalDiagnosticReceivedEventArgs.get_Scope
- ICoreWebView2ExperimentalDiagnosticReceivedEventArgs.get_Timestamp
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDiagnosticReceivedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDiagnosticReceivedEventArgs
  : public IUnknown
```

Event args for the `DiagnosticReceived` event on [ICoreWebView2ExperimentalDiagnosticMonitor](icorewebview2experimentaldiagnosticmonitor.md#icorewebview2experimentaldiagnosticmonitor).

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Category](#get_category) | The diagnostic category that this event belongs to.
[get_DetailsAsJson](#get_detailsasjson) | Returns category-specific diagnostic data as a JSON string.
[get_Scope](#get_scope) | The scope that originated this diagnostic signal.
[get_Timestamp](#get_timestamp) | The wall-clock time at which the runtime observed this diagnostic event, as the number of milliseconds since the UNIX epoch (1970-01-01T00:00:00Z, UTC).

Each instance represents a single diagnostic signal.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.4181

## Members

#### get_Category

The diagnostic category that this event belongs to.

> public HRESULT [get_Category](#get_category)(COREWEBVIEW2_DIAGNOSTIC_CATEGORY * value)

#### get_DetailsAsJson

Returns category-specific diagnostic data as a JSON string.

> public HRESULT [get_DetailsAsJson](#get_detailsasjson)(LPWSTR * value)

The schema for each category is documented on the corresponding `COREWEBVIEW2_DIAGNOSTIC_CATEGORY` enum value.

The runtime may include additional key-value pairs beyond the documented fields. Consumers should ignore unknown keys.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Scope

The scope that originated this diagnostic signal.

> public HRESULT [get_Scope](#get_scope)(COREWEBVIEW2_DIAGNOSTIC_SCOPE * value)

#### get_Timestamp

The wall-clock time at which the runtime observed this diagnostic event, as the number of milliseconds since the UNIX epoch (1970-01-01T00:00:00Z, UTC).

> public HRESULT [get_Timestamp](#get_timestamp)(INT64 * value)

Use this value to correlate diagnostic events with other timestamped telemetry. The value is derived from the system clock and may be affected by clock adjustments (for example, NTP).

