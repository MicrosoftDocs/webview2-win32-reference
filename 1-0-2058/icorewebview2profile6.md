---
description: 
title: WebView2 Win32 C++ ICoreWebView2Profile6
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile6
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile6
- ICoreWebView2Profile6.get_IsGeneralAutofillEnabled
- ICoreWebView2Profile6.get_IsPasswordAutosaveEnabled
- ICoreWebView2Profile6.put_IsGeneralAutofillEnabled
- ICoreWebView2Profile6.put_IsPasswordAutosaveEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile6

```
interface ICoreWebView2Profile6
  : public ICoreWebView2Profile5
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled) | Gets the `IsGeneralAutofillEnabled` property.
[get_IsPasswordAutosaveEnabled](#get_ispasswordautosaveenabled) | Gets the `IsPasswordAutosaveEnabled` property.
[put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled) | Sets the `IsGeneralAutofillEnabled` property.
[put_IsPasswordAutosaveEnabled](#put_ispasswordautosaveenabled) | Sets the `IsPasswordAutosaveEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1823.32
WebView2 Win32 Prerelease |    1.0.1829

## Members

#### get_IsGeneralAutofillEnabled

Gets the `IsGeneralAutofillEnabled` property.

> public HRESULT [get_IsGeneralAutofillEnabled](#get_isgeneralautofillenabled)(BOOL * value)

#### get_IsPasswordAutosaveEnabled

Gets the `IsPasswordAutosaveEnabled` property.

> public HRESULT [get_IsPasswordAutosaveEnabled](#get_ispasswordautosaveenabled)(BOOL * value)

#### put_IsGeneralAutofillEnabled

Sets the `IsGeneralAutofillEnabled` property.

> public HRESULT [put_IsGeneralAutofillEnabled](#put_isgeneralautofillenabled)(BOOL value)

#### put_IsPasswordAutosaveEnabled

Sets the `IsPasswordAutosaveEnabled` property.

> public HRESULT [put_IsPasswordAutosaveEnabled](#put_ispasswordautosaveenabled)(BOOL value)

