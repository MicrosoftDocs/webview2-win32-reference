---
description: 
title: WebView2 Win32 C++ ICoreWebView2ProcessFailedEventArgs2
ms.date: 09/08/2023
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

```
interface ICoreWebView2ProcessFailedEventArgs2
  : public ICoreWebView2ProcessFailedEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ExitCode](#get_exitcode) | Gets the `ExitCode` property.
[get_FrameInfosForFailedProcess](#get_frameinfosforfailedprocess) | Gets the `FrameInfosForFailedProcess` property.
[get_ProcessDescription](#get_processdescription) | Gets the `ProcessDescription` property.
[get_Reason](#get_reason) | Gets the `Reason` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.818.41
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_ExitCode

Gets the `ExitCode` property.

> public HRESULT [get_ExitCode](#get_exitcode)(INT32 * value)

#### get_FrameInfosForFailedProcess

Gets the `FrameInfosForFailedProcess` property.

> public HRESULT [get_FrameInfosForFailedProcess](#get_frameinfosforfailedprocess)(ICoreWebView2FrameInfoCollection ** value)

#### get_ProcessDescription

Gets the `ProcessDescription` property.

> public HRESULT [get_ProcessDescription](#get_processdescription)(LPWSTR * value)

#### get_Reason

Gets the `Reason` property.

> public HRESULT [get_Reason](#get_reason)(COREWEBVIEW2_PROCESS_FAILED_REASON * value)

