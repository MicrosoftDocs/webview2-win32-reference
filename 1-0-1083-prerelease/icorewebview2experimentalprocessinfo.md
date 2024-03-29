---
description: Provides a set of properties for a process in the ICoreWebView2Environment.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessInfo
ms.date: 01/14/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessInfo
---

# interface ICoreWebView2ExperimentalProcessInfo

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessInfo
  : public IUnknown
```

Provides a set of properties for a process in the ICoreWebView2Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Kind](#get_kind) | The kind of the process.
[get_ProcessId](#get_processid) | The process id of the process.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### get_Kind

The kind of the process.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_PROCESS_KIND * kind)

#### get_ProcessId

The process id of the process.

> public HRESULT [get_ProcessId](#get_processid)(INT32 * value)

