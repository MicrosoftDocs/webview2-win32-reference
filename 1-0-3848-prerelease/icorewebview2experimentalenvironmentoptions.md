---
description: Additional options used to create WebView2 Environment to manage port range configuration.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironmentOptions
ms.date: 02/09/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironmentOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironmentOptions
- ICoreWebView2ExperimentalEnvironmentOptions.GetEffectiveAllowedPortRange
- ICoreWebView2ExperimentalEnvironmentOptions.SetAllowedPortRange
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironmentOptions

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironmentOptions
  : public IUnknown
```

Additional options used to create WebView2 Environment to manage port range configuration.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetEffectiveAllowedPortRange](#geteffectiveallowedportrange) | Retrieves the effective allowed port range for the specified component scope and transport protocol.
[SetAllowedPortRange](#setallowedportrange) | Sets the allowed port range restriction for the specified scope and transport protocol.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.579

## Members

#### GetEffectiveAllowedPortRange

Retrieves the effective allowed port range for the specified component scope and transport protocol.

> public HRESULT [GetEffectiveAllowedPortRange](#geteffectiveallowedportrange)(COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE scope, COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND protocol, INT32 * minPort, INT32 * maxPort)

`GetEffectiveAllowedPortRange` returns the effective port range in the effect previously set via `SetAllowedPortRange`.

If the scope is _DEFAULT or if the specified scope is unset, then the _DEFAULT port range is returned. A range of (0, 0) means that no port range has been set.

Querying `_DEFAULT` only returns `_DEFAULT`; it does not aggregate component-specific settings. If neither `_DEFAULT` nor a component-specific scope is set, the default `(0,0)` (unset) is returned.

`GetEffectiveAllowedPortRange` Scope query   |Returned Range
--------- | ---------
Pass `_WEB_RTC` when only `_DEFAULT` is set   |Returns `_DEFAULT` range
Pass `_WEB_RTC` when `_WEB_RTC` explicitly set   |Returns `_WEB_RTC` range
Pass `_WEB_RTC` when `_DEFAULT` unset and `_WEB_RTC` unset   |Returns `(0, 0)`
Pass `_WEB_RTC` when `_DEFAULT` set and `_WEB_RTC` reset to `(0, 0)`|Returns `_DEFAULT`
Pass `_DEFAULT` when only `_WEB_RTC` set   |Returns `(0,0)`

`scope` Scope on which restrictions is applied. `protocol` Transport protocol on which restrictions is applied. `minPort` Receives the minimum allowed port number (inclusive). `maxPort` Receives the maximum allowed port number (inclusive).

#### SetAllowedPortRange

Sets the allowed port range restriction for the specified scope and transport protocol.

> public HRESULT [SetAllowedPortRange](#setallowedportrange)(COREWEBVIEW2_ALLOWED_PORT_RANGE_SCOPE scope, COREWEBVIEW2_TRANSPORT_PROTOCOL_KIND protocol, INT32 minPort, INT32 maxPort)

This API enables WebView2 to operate within enterprise network or firewall restrictions by limiting network communication to a defined port range. It provides fine-grained control by allowing port restrictions to be applied per network component scope, such as WebRTC.

Currently, only WebRTC UDP Port Range restriction is supported.

`minPort` and `maxPort` must be within the range 1025-65535 (inclusive), or must both be the sentinel value 0. `minPort` must be less than or equal to `maxPort`. If `minPort` equals `maxPort`, the range represents a single port.

Calls with invalid ranges fail with `E_INVALIDARG`.

A component-specific scope (e.g. _WEB_RTC) always takes precedence over _DEFAULT for that component in `SetAllowedPortRange`. `_DEFAULT` defines the port range restrictions for all components without specific overrides. Passing `(0, 0)` for a component scope unset its specific range restriction and inherit range restriction from `_DEFAULT`. If `_DEFAULT` is set and a specific scope is unset, that component inherits `_DEFAULT`. Passing `(1025,65535)` for a component scope make port range unrestricted for that component.

Scope State   |Behaviour
--------- | ---------
Only `_DEFAULT` is set   |`_DEFAULT` applies port range restrictions to all network components
`_DEFAULT` and `_WEB_RTC` are both set   |`_WEB_RTC` port range restrictions applies to WebRTC; `_DEFAULT` applies to others
`_WEB_RTC` only is set   |`_WEB_RTC` applies port range restrictions only to WebRTC; others unrestricted
`_DEFAULT` set and `_WEB_RTC` reset to `(0,0)`|`_DEFAULT` applies port range restrictions to all and WebRTC inherits `_DEFAULT`
`_DEFAULT` set and `_WEB_RTC` set to `(1025,65535)`|`_DEFAULT` applies port range restrictions to all except WebRTC which is unrestricted

`scope` Scope on which restrictions will apply. `protocol` Transport protocol on which restrictions will apply. `minPort` The minimum allowed port number (inclusive). `maxPort` The maximum allowed port number (inclusive).

