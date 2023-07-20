---
description: Event args for the `ScriptDialogOpening` event.
title: WebView2 Win32 C++ ICoreWebView2ScriptDialogOpeningEventArgs
ms.date: 07/20/2023
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

Event args for the `ScriptDialogOpening` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Accept](#accept) | The host may run this to respond with **OK** to `confirm`, `prompt`, and `beforeunload` dialogs.
[get_DefaultText](#get_defaulttext) | The second parameter passed to the JavaScript prompt dialog.
[get_Kind](#get_kind) | The kind of JavaScript dialog box.
[get_Message](#get_message) | The message of the dialog box.
[get_ResultText](#get_resulttext) | The return value from the JavaScript prompt function if `Accept` is run.
[get_Uri](#get_uri) | The URI of the page that requested the dialog box.
[GetDeferral](#getdeferral) | Returns an ICoreWebView2Deferral object.
[put_ResultText](#put_resulttext) | Sets the `ResultText` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Accept

The host may run this to respond with **OK** to `confirm`, `prompt`, and `beforeunload` dialogs.

> public HRESULT [Accept](#accept)()

Do not run this method to indicate cancel. From JavaScript, this means that the `confirm` and `beforeunload` function returns `TRUE` if `Accept` is run. And for the prompt function it returns the value of `ResultText` if `Accept` is run and otherwise returns `FALSE`.

#### get_DefaultText

The second parameter passed to the JavaScript prompt dialog.

> public HRESULT [get_DefaultText](#get_defaulttext)(LPWSTR * defaultText)

The result of the prompt JavaScript function uses this value as the default value.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Kind

The kind of JavaScript dialog box.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_SCRIPT_DIALOG_KIND * kind)

`alert`, `confirm`, `prompt`, or `beforeunload`.

#### get_Message

The message of the dialog box.

> public HRESULT [get_Message](#get_message)(LPWSTR * message)

From JavaScript this is the first parameter passed to `alert`, `confirm`, and `prompt` and is empty for `beforeunload`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ResultText

The return value from the JavaScript prompt function if `Accept` is run.

> public HRESULT [get_ResultText](#get_resulttext)(LPWSTR * resultText)

This value is ignored for dialog kinds other than prompt. If `Accept` is not run, this value is ignored and `FALSE` is returned from prompt.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Uri

The URI of the page that requested the dialog box.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * uri)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetDeferral

Returns an ICoreWebView2Deferral object.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use this operation to complete the event at a later time.

#### put_ResultText

Sets the `ResultText` property.

> public HRESULT [put_ResultText](#put_resulttext)(LPCWSTR resultText)

