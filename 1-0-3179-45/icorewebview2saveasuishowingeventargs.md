---
description: The event args for `SaveAsUIShowing` event.
title: WebView2 Win32 C++ ICoreWebView2SaveAsUIShowingEventArgs
ms.date: 04/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SaveAsUIShowingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2SaveAsUIShowingEventArgs
- ICoreWebView2SaveAsUIShowingEventArgs.get_AllowReplace
- ICoreWebView2SaveAsUIShowingEventArgs.get_Cancel
- ICoreWebView2SaveAsUIShowingEventArgs.get_ContentMimeType
- ICoreWebView2SaveAsUIShowingEventArgs.get_Kind
- ICoreWebView2SaveAsUIShowingEventArgs.get_SaveAsFilePath
- ICoreWebView2SaveAsUIShowingEventArgs.get_SuppressDefaultDialog
- ICoreWebView2SaveAsUIShowingEventArgs.GetDeferral
- ICoreWebView2SaveAsUIShowingEventArgs.put_AllowReplace
- ICoreWebView2SaveAsUIShowingEventArgs.put_Cancel
- ICoreWebView2SaveAsUIShowingEventArgs.put_Kind
- ICoreWebView2SaveAsUIShowingEventArgs.put_SaveAsFilePath
- ICoreWebView2SaveAsUIShowingEventArgs.put_SuppressDefaultDialog
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SaveAsUIShowingEventArgs

```
interface ICoreWebView2SaveAsUIShowingEventArgs
  : public IUnknown
```

The event args for `SaveAsUIShowing` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AllowReplace](#get_allowreplace) | Gets the `AllowReplace` property.
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_ContentMimeType](#get_contentmimetype) | Get the Mime type of content to be saved.
[get_Kind](#get_kind) | Gets the `Kind` property.
[get_SaveAsFilePath](#get_saveasfilepath) | Gets the `SaveAsFilePath` property.
[get_SuppressDefaultDialog](#get_suppressdefaultdialog) | Gets the `SuppressDefaultDialog` property.
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.
[put_AllowReplace](#put_allowreplace) | `AllowReplace` allows user to control what happens when a file already exists in the file path to which the Save As operation is saving.
[put_Cancel](#put_cancel) | Sets the `Cancel` property.
[put_Kind](#put_kind) | Sets the `Kind` property to save documents of different kinds.
[put_SaveAsFilePath](#put_saveasfilepath) | Set the `SaveAsFilePath` property for Save As.
[put_SuppressDefaultDialog](#put_suppressdefaultdialog) | Sets the `SuppressDefaultDialog` property, which indicates whether the system default dialog is suppressed.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2739.15
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### get_AllowReplace

Gets the `AllowReplace` property.

> public HRESULT [get_AllowReplace](#get_allowreplace)(BOOL * value)

#### get_Cancel

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_ContentMimeType

Get the Mime type of content to be saved.

> public HRESULT [get_ContentMimeType](#get_contentmimetype)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Kind

Gets the `Kind` property.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_SAVE_AS_KIND * value)

#### get_SaveAsFilePath

Gets the `SaveAsFilePath` property.

> public HRESULT [get_SaveAsFilePath](#get_saveasfilepath)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_SuppressDefaultDialog

Gets the `SuppressDefaultDialog` property.

> public HRESULT [get_SuppressDefaultDialog](#get_suppressdefaultdialog)(BOOL * value)

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md#icorewebview2deferral) ** value)

This will defer showing the default Save As dialog and performing the Save As operation.

#### put_AllowReplace

`AllowReplace` allows user to control what happens when a file already exists in the file path to which the Save As operation is saving.

> public HRESULT [put_AllowReplace](#put_allowreplace)(BOOL value)

Setting this property to `TRUE` allows existing files to be replaced. Setting this property to `FALSE` will not replace existing files and will return `COREWEBVIEW2_SAVE_AS_UI_RESULT_FILE_ALREADY_EXISTS`.

The default value is `FALSE`.

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

Set this property to `TRUE` to cancel the Save As action and prevent the download from starting. ShowSaveAsUI returns `COREWEBVIEW2_SAVE_AS_UI_RESULT_CANCELLED` in this case. The default value is `FALSE`.

#### put_Kind

Sets the `Kind` property to save documents of different kinds.

> public HRESULT [put_Kind](#put_kind)(COREWEBVIEW2_SAVE_AS_KIND value)

See the `COREWEBVIEW2_SAVE_AS_KIND` enum for a description of the different options. If the kind is not allowed for the current document, ShowSaveAsUI returns `COREWEBVIEW2_SAVE_AS_UI_RESULT_KIND_NOT_SUPPORTED`.

The default value is `COREWEBVIEW2_SAVE_AS_KIND_DEFAULT`.

#### put_SaveAsFilePath

Set the `SaveAsFilePath` property for Save As.

> public HRESULT [put_SaveAsFilePath](#put_saveasfilepath)(LPCWSTR value)

`SaveAsFilePath` is an absolute path of the location. It includes the file name and extension. If `SaveAsFilePath` is not valid (for example, the root drive does not exist), Save As is denied and `COREWEBVIEW2_SAVE_AS_INVALID_PATH` is returned.

If the associated download completes successfully, a target file is saved at this location. If the Kind property is `COREWEBVIEW2_SAVE_AS_KIND_COMPLETE`, there will be an additional directory with resources files.

The default value is a system suggested path, based on users' local environment.

#### put_SuppressDefaultDialog

Sets the `SuppressDefaultDialog` property, which indicates whether the system default dialog is suppressed.

> public HRESULT [put_SuppressDefaultDialog](#put_suppressdefaultdialog)(BOOL value)

When `SuppressDefaultDialog` is `FALSE`, the default Save As dialog is shown and the values assigned through `SaveAsFilePath`, `AllowReplace` and `Kind` are ignored when the event args invoke completed.

Set `SuppressDefaultDialog` to `TRUE` to perform a silent Save As. When `SuppressDefaultDialog` is `TRUE`, the system dialog is skipped and the `SaveAsFilePath`, `AllowReplace` and `Kind` values are used.

The default value is FALSE.

