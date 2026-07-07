---
description: A continuation of the ICoreWebView2ProcessFailedEventArgs3 interface for getting the crash report associated with the process failure.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessFailedEventArgs2
ms.date: 06/30/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessFailedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProcessFailedEventArgs2
- ICoreWebView2ExperimentalProcessFailedEventArgs2.get_CrashReport
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProcessFailedEventArgs2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessFailedEventArgs2
  : public IUnknown
```

A continuation of the [ICoreWebView2ProcessFailedEventArgs3](icorewebview2processfailedeventargs3.md#icorewebview2processfailedeventargs3) interface for getting the crash report associated with the process failure.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CrashReport](#get_crashreport) | The crash report for this process failure, or `null` if no crash report is available (normal exit, external kill, launch failure, hang, or crash-type failure that produced no report).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_CrashReport

The crash report for this process failure, or `null` if no crash report is available (normal exit, external kill, launch failure, hang, or crash-type failure that produced no report).

> public HRESULT [get_CrashReport](#get_crashreport)([ICoreWebView2ExperimentalCrashReport](icorewebview2experimentalcrashreport.md#icorewebview2experimentalcrashreport) ** value)

