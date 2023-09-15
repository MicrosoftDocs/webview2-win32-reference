---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings4
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings4
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings4
- ICoreWebView2Settings4.get_IsGeneralAutofillEnabled
- ICoreWebView2Settings4.get_IsPasswordAutosaveEnabled
- ICoreWebView2Settings4.put_IsGeneralAutofillEnabled
- ICoreWebView2Settings4.put_IsPasswordAutosaveEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings4

```
interface ICoreWebView2Settings4
  : public ICoreWebView2Settings3
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
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

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

