---
description: A continuation of the ICoreWebView2ProcessFailedEventArgs interface.
title: WebView2 Win32 C++ ICoreWebView2ProcessFailedEventArgs2
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessFailedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessFailedEventArgs2
- ICoreWebView2ProcessFailedEventArgs2.get_ExitCode
- ICoreWebView2ProcessFailedEventArgs2.get_FrameInfosForFailedProcess
- ICoreWebView2ProcessFailedEventArgs2.get_ProcessDescription
- ICoreWebView2ProcessFailedEventArgs2.get_Reason
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessFailedEventArgs2

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProcessFailedEventArgs2
  : public ICoreWebView2ProcessFailedEventArgs
```

A continuation of the [ICoreWebView2ProcessFailedEventArgs](icorewebview2processfailedeventargs.md#icorewebview2processfailedeventargs) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ExitCode](#get_exitcode) | The exit code of the failing process, for telemetry purposes.
[get_FrameInfosForFailedProcess](#get_frameinfosforfailedprocess) | The collection of `FrameInfo`s for frames in the [ICoreWebView2](icorewebview2.md#icorewebview2) that were being rendered by the failed process.
[get_ProcessDescription](#get_processdescription) | Description of the process assigned by the WebView2 Runtime.
[get_Reason](#get_reason) | The reason for the process failure.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.818.41
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_ExitCode

The exit code of the failing process, for telemetry purposes.

> public HRESULT [get_ExitCode](#get_exitcode)(int * exitCode)

The exit code is always `STILL_ACTIVE` (`259`) when `ProcessFailedKind` is `COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE`.

#### get_FrameInfosForFailedProcess

The collection of `FrameInfo`s for frames in the [ICoreWebView2](icorewebview2.md#icorewebview2) that were being rendered by the failed process.

> public HRESULT [get_FrameInfosForFailedProcess](#get_frameinfosforfailedprocess)([ICoreWebView2FrameInfoCollection](icorewebview2frameinfocollection.md#icorewebview2frameinfocollection) ** frames)

The content in these frames is replaced with an error page. This is only available when `ProcessFailedKind` is `COREWEBVIEW2_PROCESS_FAILED_KIND_FRAME_RENDER_PROCESS_EXITED`; `frames` is `null` for all other process failure kinds, including the case in which the failed process was the renderer for the main frame and subframes within it, for which the failure kind is `COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED`.

#### get_ProcessDescription

Description of the process assigned by the WebView2 Runtime.

> public HRESULT [get_ProcessDescription](#get_processdescription)(LPWSTR * processDescription)

This is a technical English term appropriate for logging or development purposes, and not localized for the end user. It applies to utility processes (for example, "Audio Service", "Video Capture") and plugin processes (for example, "Flash"). The returned `processDescription` is empty if the WebView2 Runtime did not assign a description to the process.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Reason

The reason for the process failure.

> public HRESULT [get_Reason](#get_reason)(COREWEBVIEW2_PROCESS_FAILED_REASON * reason)

Some of the reasons are only applicable to specific values of `ICoreWebView2ProcessFailedEventArgs::ProcessFailedKind`, and the following `ProcessFailedKind` values always return the indicated reason value:

ProcessFailedKind   |Reason
--------- | ---------
COREWEBVIEW2_PROCESS_FAILED_KIND_BROWSER_PROCESS_EXITED   |COREWEBVIEW2_PROCESS_FAILED_REASON_UNEXPECTED
COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_UNRESPONSIVE   |COREWEBVIEW2_PROCESS_FAILED_REASON_UNRESPONSIVE

For other `ProcessFailedKind` values, the reason may be any of the reason values. To learn about what these values mean, see `COREWEBVIEW2_PROCESS_FAILED_REASON`.

