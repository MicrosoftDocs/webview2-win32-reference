---
description: The event args for `SaveFileSecurityCheckStarting` event.
title: WebView2 Win32 C++ ICoreWebView2SaveFileSecurityCheckStartingEventArgs
ms.date: 04/29/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SaveFileSecurityCheckStartingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.get_CancelSave
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.get_DocumentOriginUri
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.get_FileExtension
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.get_FilePath
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.get_SuppressDefaultPolicy
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.GetDeferral
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.put_CancelSave
- ICoreWebView2SaveFileSecurityCheckStartingEventArgs.put_SuppressDefaultPolicy
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SaveFileSecurityCheckStartingEventArgs

```
interface ICoreWebView2SaveFileSecurityCheckStartingEventArgs
  : public IUnknown
```

The event args for `SaveFileSecurityCheckStarting` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_CancelSave](#get_cancelsave) | Gets the `CancelSave` property.
[get_DocumentOriginUri](#get_documentoriginuri) | Get the document origin URI of this file save operation.
[get_FileExtension](#get_fileextension) | Get the extension of file to be saved.
[get_FilePath](#get_filepath) | Get the full path of file to be saved.
[get_SuppressDefaultPolicy](#get_suppressdefaultpolicy) | Gets the `SuppressDefaultPolicy` property.
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_CancelSave](#put_cancelsave) | Set if cancel the upcoming save/download.
[put_SuppressDefaultPolicy](#put_suppressdefaultpolicy) | Set if the default policy checking and security warning will be suppressed.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2849.39
WebView2 Win32 Prerelease |    1.0.2895

## Members

#### get_CancelSave

Gets the `CancelSave` property.

> public HRESULT [get_CancelSave](#get_cancelsave)(BOOL * value)

#### get_DocumentOriginUri

Get the document origin URI of this file save operation.

> public HRESULT [get_DocumentOriginUri](#get_documentoriginuri)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_FileExtension

Get the extension of file to be saved.

> public HRESULT [get_FileExtension](#get_fileextension)(LPWSTR * value)

The file extension is the extension portion of the FilePath, preserving original case.

Only final extension with period "." will be provided. For example, "*.tar.gz" is a double extension, where the ".gz" will be its final extension.

File extension can be empty, if the file name has no extension at all.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_FilePath

Get the full path of file to be saved.

> public HRESULT [get_FilePath](#get_filepath)(LPWSTR * value)

This includes the file name and extension.

This method doesn't provide path validation, the returned string may longer than MAX_PATH.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_SuppressDefaultPolicy

Gets the `SuppressDefaultPolicy` property.

> public HRESULT [get_SuppressDefaultPolicy](#get_suppressdefaultpolicy)(BOOL * value)

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** value)

Use this operation to complete the SaveFileSecurityCheckStartingEvent.

The default policy checking and any default UI will be blocked temporarily, saving file to local won't start, until the deferral is completed.

#### put_CancelSave

Set if cancel the upcoming save/download.

> public HRESULT [put_CancelSave](#put_cancelsave)(BOOL value)

`TRUE` means the action will be cancelled before validations in default policy.

The default value is `FALSE`.

#### put_SuppressDefaultPolicy

Set if the default policy checking and security warning will be suppressed.

> public HRESULT [put_SuppressDefaultPolicy](#put_suppressdefaultpolicy)(BOOL value)

`TRUE` means it will be suppressed.

The default value is `FALSE`.

