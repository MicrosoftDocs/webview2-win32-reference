---
description: A continuation of the ICoreWebView2Frame interface to support UseOverrideTimerWakeInterval property.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalFrame7
ms.date: 01/13/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalFrame7
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalFrame7
- ICoreWebView2ExperimentalFrame7.get_UseOverrideTimerWakeInterval
- ICoreWebView2ExperimentalFrame7.put_UseOverrideTimerWakeInterval
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalFrame7

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalFrame7
  : public IUnknown
```

A continuation of the [ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) interface to support UseOverrideTimerWakeInterval property.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UseOverrideTimerWakeInterval](#get_useoverridetimerwakeinterval) | Gets the `UseOverrideTimerWakeInterval` property.
[put_UseOverrideTimerWakeInterval](#put_useoverridetimerwakeinterval) | Indicates whether timer wake interval should be overridden for the frame.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### get_UseOverrideTimerWakeInterval

Gets the `UseOverrideTimerWakeInterval` property.

> public HRESULT [get_UseOverrideTimerWakeInterval](#get_useoverridetimerwakeinterval)(BOOL * value)

#### put_UseOverrideTimerWakeInterval

Indicates whether timer wake interval should be overridden for the frame.

> public HRESULT [put_UseOverrideTimerWakeInterval](#put_useoverridetimerwakeinterval)(BOOL value)

When `TRUE`, timers in the frame will run at most at the interval set by `PreferredOverrideTimerWakeIntervalInMilliseconds`. All frames in the WebView that set this property to `TRUE` are subject to the same timer wake interval. When `FALSE`, and for main frame, the timer wake interval will be determined by page state and the corresponding interval value for that state, set by the matching property in `CoreWebView2Settings`. Defaults to `FALSE` unless set otherwise.

