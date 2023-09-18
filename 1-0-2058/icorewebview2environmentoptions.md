---
description: 
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions
- ICoreWebView2EnvironmentOptions.get_AdditionalBrowserArguments
- ICoreWebView2EnvironmentOptions.get_AllowSingleSignOnUsingOSPrimaryAccount
- ICoreWebView2EnvironmentOptions.get_Language
- ICoreWebView2EnvironmentOptions.get_TargetCompatibleBrowserVersion
- ICoreWebView2EnvironmentOptions.put_AdditionalBrowserArguments
- ICoreWebView2EnvironmentOptions.put_AllowSingleSignOnUsingOSPrimaryAccount
- ICoreWebView2EnvironmentOptions.put_Language
- ICoreWebView2EnvironmentOptions.put_TargetCompatibleBrowserVersion
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions

```
interface ICoreWebView2EnvironmentOptions
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalBrowserArguments](#get_additionalbrowserarguments) | Gets the `AdditionalBrowserArguments` property.
[get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount) | Gets the `AllowSingleSignOnUsingOSPrimaryAccount` property.
[get_Language](#get_language) | Gets the `Language` property.
[get_TargetCompatibleBrowserVersion](#get_targetcompatiblebrowserversion) | Gets the `TargetCompatibleBrowserVersion` property.
[put_AdditionalBrowserArguments](#put_additionalbrowserarguments) | Sets the `AdditionalBrowserArguments` property.
[put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount) | Sets the `AllowSingleSignOnUsingOSPrimaryAccount` property.
[put_Language](#put_language) | Sets the `Language` property.
[put_TargetCompatibleBrowserVersion](#put_targetcompatiblebrowserversion) | Sets the `TargetCompatibleBrowserVersion` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.488
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_AdditionalBrowserArguments

Gets the `AdditionalBrowserArguments` property.

> public HRESULT [get_AdditionalBrowserArguments](#get_additionalbrowserarguments)(LPWSTR * value)

#### get_AllowSingleSignOnUsingOSPrimaryAccount

Gets the `AllowSingleSignOnUsingOSPrimaryAccount` property.

> public HRESULT [get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount)(BOOL * value)

#### get_Language

Gets the `Language` property.

> public HRESULT [get_Language](#get_language)(LPWSTR * value)

#### get_TargetCompatibleBrowserVersion

Gets the `TargetCompatibleBrowserVersion` property.

> public HRESULT [get_TargetCompatibleBrowserVersion](#get_targetcompatiblebrowserversion)(LPWSTR * value)

#### put_AdditionalBrowserArguments

Sets the `AdditionalBrowserArguments` property.

> public HRESULT [put_AdditionalBrowserArguments](#put_additionalbrowserarguments)(LPCWSTR value)

#### put_AllowSingleSignOnUsingOSPrimaryAccount

Sets the `AllowSingleSignOnUsingOSPrimaryAccount` property.

> public HRESULT [put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount)(BOOL value)

#### put_Language

Sets the `Language` property.

> public HRESULT [put_Language](#put_language)(LPCWSTR value)

#### put_TargetCompatibleBrowserVersion

Sets the `TargetCompatibleBrowserVersion` property.

> public HRESULT [put_TargetCompatibleBrowserVersion](#put_targetcompatiblebrowserversion)(LPCWSTR value)

