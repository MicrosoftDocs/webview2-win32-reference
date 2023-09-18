---
description: 
title: WebView2 Win32 C++ ICoreWebView2ScriptDialogOpeningEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ScriptDialogOpeningEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ScriptDialogOpeningEventArgs
- ICoreWebView2ScriptDialogOpeningEventArgs.Accept
- ICoreWebView2ScriptDialogOpeningEventArgs.get_DefaultText
- ICoreWebView2ScriptDialogOpeningEventArgs.get_Kind
- ICoreWebView2ScriptDialogOpeningEventArgs.get_Message
- ICoreWebView2ScriptDialogOpeningEventArgs.get_ResultText
- ICoreWebView2ScriptDialogOpeningEventArgs.get_Uri
- ICoreWebView2ScriptDialogOpeningEventArgs.GetDeferral
- ICoreWebView2ScriptDialogOpeningEventArgs.put_ResultText
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ScriptDialogOpeningEventArgs

```
interface ICoreWebView2ScriptDialogOpeningEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Accept](#accept) | 
[get_DefaultText](#get_defaulttext) | Gets the `DefaultText` property.
[get_Kind](#get_kind) | Gets the `Kind` property.
[get_Message](#get_message) | Gets the `Message` property.
[get_ResultText](#get_resulttext) | Gets the `ResultText` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[GetDeferral](#getdeferral) | 
[put_ResultText](#put_resulttext) | Sets the `ResultText` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Accept

> public HRESULT [Accept](#accept)()

#### get_DefaultText

Gets the `DefaultText` property.

> public HRESULT [get_DefaultText](#get_defaulttext)(LPWSTR * value)

#### get_Kind

Gets the `Kind` property.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_SCRIPT_DIALOG_KIND * value)

#### get_Message

Gets the `Message` property.

> public HRESULT [get_Message](#get_message)(LPWSTR * value)

#### get_ResultText

Gets the `ResultText` property.

> public HRESULT [get_ResultText](#get_resulttext)(LPWSTR * value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_ResultText

Sets the `ResultText` property.

> public HRESULT [put_ResultText](#put_resulttext)(LPCWSTR value)

