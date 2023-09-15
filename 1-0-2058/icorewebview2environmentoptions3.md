---
description: 
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions3
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions3
- ICoreWebView2EnvironmentOptions3.get_IsCustomCrashReportingEnabled
- ICoreWebView2EnvironmentOptions3.put_IsCustomCrashReportingEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions3

```
interface ICoreWebView2EnvironmentOptions3
  : public ICoreWebView2EnvironmentOptions2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsCustomCrashReportingEnabled](#get_iscustomcrashreportingenabled) | Gets the `IsCustomCrashReportingEnabled` property.
[put_IsCustomCrashReportingEnabled](#put_iscustomcrashreportingenabled) | Sets the `IsCustomCrashReportingEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1518.46
WebView2 Win32 Prerelease |    1.0.1549

## Members

#### get_IsCustomCrashReportingEnabled

Gets the `IsCustomCrashReportingEnabled` property.

> public HRESULT [get_IsCustomCrashReportingEnabled](#get_iscustomcrashreportingenabled)(BOOL * value)

#### put_IsCustomCrashReportingEnabled

Sets the `IsCustomCrashReportingEnabled` property.

> public HRESULT [put_IsCustomCrashReportingEnabled](#put_iscustomcrashreportingenabled)(BOOL value)

