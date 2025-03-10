---
description: A continuation of the ICoreWebView2Settings interface to support timer wake intervals.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSettings9
ms.date: 02/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSettings9
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSettings9
- ICoreWebView2ExperimentalSettings9.get_PreferredBackgroundTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.get_PreferredForegroundTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.get_PreferredIntensiveTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.get_PreferredOverrideTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.put_PreferredBackgroundTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.put_PreferredForegroundTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.put_PreferredIntensiveTimerWakeIntervalInMilliseconds
- ICoreWebView2ExperimentalSettings9.put_PreferredOverrideTimerWakeIntervalInMilliseconds
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSettings9

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSettings9
  : public IUnknown
```

A continuation of the [ICoreWebView2Settings](icorewebview2settings.md#icorewebview2settings) interface to support timer wake intervals.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_PreferredBackgroundTimerWakeIntervalInMilliseconds](#get_preferredbackgroundtimerwakeintervalinmilliseconds) | Gets the `PreferredBackgroundTimerWakeIntervalInMilliseconds` property.
[get_PreferredForegroundTimerWakeIntervalInMilliseconds](#get_preferredforegroundtimerwakeintervalinmilliseconds) | Gets the `PreferredForegroundTimerWakeIntervalInMilliseconds` property.
[get_PreferredIntensiveTimerWakeIntervalInMilliseconds](#get_preferredintensivetimerwakeintervalinmilliseconds) | Gets the `PreferredIntensiveTimerWakeIntervalInMilliseconds` property.
[get_PreferredOverrideTimerWakeIntervalInMilliseconds](#get_preferredoverridetimerwakeintervalinmilliseconds) | Gets the `PreferredOverrideTimerWakeIntervalInMilliseconds` property.
[put_PreferredBackgroundTimerWakeIntervalInMilliseconds](#put_preferredbackgroundtimerwakeintervalinmilliseconds) | The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), when the WebView is in background state, with no intensive throttling.
[put_PreferredForegroundTimerWakeIntervalInMilliseconds](#put_preferredforegroundtimerwakeintervalinmilliseconds) | The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), when the WebView is in foreground state.
[put_PreferredIntensiveTimerWakeIntervalInMilliseconds](#put_preferredintensivetimerwakeintervalinmilliseconds) | The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), when the WebView is in background state with intensive throttling.
[put_PreferredOverrideTimerWakeIntervalInMilliseconds](#put_preferredoverridetimerwakeintervalinmilliseconds) | The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), in frames whose `UseOverrideTimerWakeInterval` property is set to `TRUE`, regardless of whether they are in foreground or background state.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### get_PreferredBackgroundTimerWakeIntervalInMilliseconds

Gets the `PreferredBackgroundTimerWakeIntervalInMilliseconds` property.

> public HRESULT [get_PreferredBackgroundTimerWakeIntervalInMilliseconds](#get_preferredbackgroundtimerwakeintervalinmilliseconds)(INT32 * value)

#### get_PreferredForegroundTimerWakeIntervalInMilliseconds

Gets the `PreferredForegroundTimerWakeIntervalInMilliseconds` property.

> public HRESULT [get_PreferredForegroundTimerWakeIntervalInMilliseconds](#get_preferredforegroundtimerwakeintervalinmilliseconds)(INT32 * value)

#### get_PreferredIntensiveTimerWakeIntervalInMilliseconds

Gets the `PreferredIntensiveTimerWakeIntervalInMilliseconds` property.

> public HRESULT [get_PreferredIntensiveTimerWakeIntervalInMilliseconds](#get_preferredintensivetimerwakeintervalinmilliseconds)(INT32 * value)

#### get_PreferredOverrideTimerWakeIntervalInMilliseconds

Gets the `PreferredOverrideTimerWakeIntervalInMilliseconds` property.

> public HRESULT [get_PreferredOverrideTimerWakeIntervalInMilliseconds](#get_preferredoverridetimerwakeintervalinmilliseconds)(INT32 * value)

#### put_PreferredBackgroundTimerWakeIntervalInMilliseconds

The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), when the WebView is in background state, with no intensive throttling.

> public HRESULT [put_PreferredBackgroundTimerWakeIntervalInMilliseconds](#put_preferredbackgroundtimerwakeintervalinmilliseconds)(INT32 value)

A WebView is in background state when its `IsVisible` property is `FALSE`. Intensive throttling is a substate of background state. For more details about intensive throttling, see [Intensive throttling of Javascript timer wake ups](https://chromestatus.com/feature/4718288976216064).

A wake up interval is the amount of time that needs to pass before the WebView2 Runtime checks for new timer tasks to run.

The WebView2 Runtime will try to respect the preferred interval set by the application, but the effective value will be constrained by resource and platform limitations. Setting a value of `0` means a preference of 0 ms between timer wake ups. The default value is a constant determined by the running version of the WebView2 Runtime. Setting the value of this property will take effect immediately. All other background state policies (including intensive throttling) are effective independently of this setting.

For example, an application might use a background value of 100 ms to relax the default background value (usually 1000 ms). In this case, timers will run at most every 100 ms.

#### put_PreferredForegroundTimerWakeIntervalInMilliseconds

The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), when the WebView is in foreground state.

> public HRESULT [put_PreferredForegroundTimerWakeIntervalInMilliseconds](#put_preferredforegroundtimerwakeintervalinmilliseconds)(INT32 value)

A WebView is in foreground state when its `IsVisible` property is `TRUE`. This aligns to the Chromium concept of foreground, which means programmatically visible, even if occluded. For more details, see [Page Visibility API](https://developer.mozilla.org/docs/Web/API/Page_Visibility_API).

A wake up interval is the amount of time that needs to pass before the WebView2 Runtime checks for new timer tasks to run.

The WebView2 Runtime will try to respect the preferred interval set by the application, but the effective value will be constrained by resource and platform limitations. Setting a value of `0` means a preference of 0 ms between timer wake ups. The default value is a constant determined by the running version of the WebView2 Runtime. Setting the value of this property will take effect immediately.

For example, an application might use a foreground value of 30 ms for moderate throttling scenarios. In this case, timers will run at most every 30 ms. Or the application could get and match the default background value (usually 1000 ms).

#### put_PreferredIntensiveTimerWakeIntervalInMilliseconds

The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), when the WebView is in background state with intensive throttling.

> public HRESULT [put_PreferredIntensiveTimerWakeIntervalInMilliseconds](#put_preferredintensivetimerwakeintervalinmilliseconds)(INT32 value)

Intensive throttling is a substate of background state. For more details about intensive throttling, see [Intensive throttling of Javascript timer wake ups](https://chromestatus.com/feature/4718288976216064).

A wake up interval is the amount of time that needs to pass before the WebView2 Runtime checks for new timer tasks to run.

The WebView2 Runtime will try to respect the preferred interval set by the application, but the effective value will be constrained by resource and platform limitations. Setting a value of `0` means a preference of 0 ms between timer wake ups. The default value is a constant determined by the running version of the WebView2 Runtime. Setting the value of this property will take effect immediately.

#### put_PreferredOverrideTimerWakeIntervalInMilliseconds

The preferred timer wake up interval (in milliseconds) to use for timer tasks in script (`setTimeout` and `setInterval`), in frames whose `UseOverrideTimerWakeInterval` property is set to `TRUE`, regardless of whether they are in foreground or background state.

> public HRESULT [put_PreferredOverrideTimerWakeIntervalInMilliseconds](#put_preferredoverridetimerwakeintervalinmilliseconds)(INT32 value)

This is a category specific to WebView2 with no corresponding state in the Chromium tab state model.

A wake up interval is the amount of time that needs to pass before the WebView2 Runtime checks for new timer tasks to run.

The WebView2 Runtime will try to respect the preferred interval set by the application, but the effective value will be constrained by resource and platform limitations. Setting a value of `0` means a preference of 0 ms between timer wake ups. The default value is a constant determined by the running version of the WebView2 Runtime. Setting the value of this property will take effect immediately.

For example, an application might use an override timer wake interval of 30 ms to reduce resource consumption from third party frames in the WebView. In this case, timers will run at most every 30 ms.

