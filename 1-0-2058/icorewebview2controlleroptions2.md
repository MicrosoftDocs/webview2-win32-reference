---
description: 
title: WebView2 Win32 C++ ICoreWebView2ControllerOptions2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ControllerOptions2
topic_type: 
- APIRef
api_name:
- ICoreWebView2ControllerOptions2
- ICoreWebView2ControllerOptions2.get_ScriptLocale
- ICoreWebView2ControllerOptions2.put_ScriptLocale
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ControllerOptions2

```
interface ICoreWebView2ControllerOptions2
  : public ICoreWebView2ControllerOptions
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ScriptLocale](#get_scriptlocale) | Gets the `ScriptLocale` property.
[put_ScriptLocale](#put_scriptlocale) | Sets the `ScriptLocale` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_ScriptLocale

Gets the `ScriptLocale` property.

> public HRESULT [get_ScriptLocale](#get_scriptlocale)(LPWSTR * value)

#### put_ScriptLocale

Sets the `ScriptLocale` property.

> public HRESULT [put_ScriptLocale](#put_scriptlocale)(LPCWSTR value)

