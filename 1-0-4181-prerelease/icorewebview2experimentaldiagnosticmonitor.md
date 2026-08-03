---
description: A diagnostic monitor that receives diagnostic signals from all layers - WebView, Profile, and Environment.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDiagnosticMonitor
ms.date: 07/27/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDiagnosticMonitor
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDiagnosticMonitor
- ICoreWebView2ExperimentalDiagnosticMonitor.add_DiagnosticReceived
- ICoreWebView2ExperimentalDiagnosticMonitor.Close
- ICoreWebView2ExperimentalDiagnosticMonitor.remove_DiagnosticReceived
- ICoreWebView2ExperimentalDiagnosticMonitor.RemoveDiagnosticFilter
- ICoreWebView2ExperimentalDiagnosticMonitor.SetDiagnosticFilter
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDiagnosticMonitor

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDiagnosticMonitor
  : public IUnknown
```

A diagnostic monitor that receives diagnostic signals from all layers - WebView, Profile, and Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DiagnosticReceived](#add_diagnosticreceived) | Adds an event handler for the `DiagnosticReceived` event.
[Close](#close) | Release the diagnostic subscription and any registered handlers.
[remove_DiagnosticReceived](#remove_diagnosticreceived) | Removes an event handler previously added with `add_DiagnosticReceived`.
[RemoveDiagnosticFilter](#removediagnosticfilter) | Removes the diagnostic filter for the specified category.
[SetDiagnosticFilter](#setdiagnosticfilter) | Sets a diagnostic filter for the specified category.

Created via [ICoreWebView2ExperimentalEnvironment16::CreateDiagnosticMonitor](icorewebview2experimentalenvironment16.md#creatediagnosticmonitor). Each monitor has its own filters and event handlers, allowing multiple independent consumers (for example, one for telemetry, one for a debug panel).

The monitor is active from creation until it is released. Releasing the monitor automatically stops all events and clears all filters.

All members of this interface must be called on the same thread that created the [ICoreWebView2Environment](icorewebview2environment.md#icorewebview2environment). Calling from a different thread returns `RPC_E_WRONG_THREAD`. Handlers must not block this thread.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### add_DiagnosticReceived

Adds an event handler for the `DiagnosticReceived` event.

> public HRESULT [add_DiagnosticReceived](#add_diagnosticreceived)([ICoreWebView2ExperimentalDiagnosticReceivedEventHandler](icorewebview2experimentaldiagnosticreceivedeventhandler.md#icorewebview2experimentaldiagnosticreceivedeventhandler) * eventHandler, EventRegistrationToken * token)

Subscribes to diagnostic events on this monitor. The handler is invoked on the thread that created the environment. It fires every time a diagnostic signal passes a filter set with `SetDiagnosticFilter`.

Multiple handlers can be registered. They are invoked in registration order.

#### Close

Release the diagnostic subscription and any registered handlers.

> public HRESULT [Close](#close)()

The application should call this API when no access to the monitor is needed any more, to ensure that the underlying resources are released timely even if the monitor object itself is not released due to some leaked reference.

#### remove_DiagnosticReceived

Removes an event handler previously added with `add_DiagnosticReceived`.

> public HRESULT [remove_DiagnosticReceived](#remove_diagnosticreceived)(EventRegistrationToken token)

#### RemoveDiagnosticFilter

Removes the diagnostic filter for the specified category.

> public HRESULT [RemoveDiagnosticFilter](#removediagnosticfilter)(COREWEBVIEW2_DIAGNOSTIC_CATEGORY category)

After this call, `DiagnosticReceived` will no longer fire for events in this category.

If no filter was previously set for the category, this method is a no-op and returns `S_OK`.

#### SetDiagnosticFilter

Sets a diagnostic filter for the specified category.

> public HRESULT [SetDiagnosticFilter](#setdiagnosticfilter)(COREWEBVIEW2_DIAGNOSTIC_CATEGORY category, LPCWSTR jsonFilter)

After this call, `DiagnosticReceived` will fire for events in this category that match the JSON criteria.

The filter JSON schema is category-specific and is documented on the corresponding `COREWEBVIEW2_DIAGNOSTIC_CATEGORY` enum value.

Pass `"{}"` as `jsonFilter` to receive all events in the category without field-level filtering.

Calling this method again for the same category replaces the previous filter for that category.

Returns `E_INVALIDARG` if `jsonFilter` is an empty string, is malformed JSON, or does not match the category's filter schema. On failure, the filter state is unchanged.

