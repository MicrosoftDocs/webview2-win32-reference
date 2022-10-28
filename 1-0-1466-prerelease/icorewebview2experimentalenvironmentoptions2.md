---
description: Additional options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironmentOptions2
ms.date: 10/31/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironmentOptions2
---

# interface ICoreWebView2ExperimentalEnvironmentOptions2

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironmentOptions2
  : public IUnknown
```

Additional options used to create WebView2 Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsCustomCrashReportingEnabled](#get_iscustomcrashreportingenabled) | When `IsCustomCrashReportingEnabled` is set to `TRUE`, Windows won't send crash data to Microsoft endpoint.
[put_IsCustomCrashReportingEnabled](#put_iscustomcrashreportingenabled) | Sets the `IsCustomCrashReportingEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1414

## Members

#### get_IsCustomCrashReportingEnabled

When `IsCustomCrashReportingEnabled` is set to `TRUE`, Windows won't send crash data to Microsoft endpoint.

> public HRESULT [get_IsCustomCrashReportingEnabled](#get_iscustomcrashreportingenabled)(BOOL * value)

`IsCustomCrashReportingEnabled` is default to be `FALSE`, in this case, WebView will respect OS consent.

#### put_IsCustomCrashReportingEnabled

Sets the `IsCustomCrashReportingEnabled` property.

> public HRESULT [put_IsCustomCrashReportingEnabled](#put_iscustomcrashreportingenabled)(BOOL value)

