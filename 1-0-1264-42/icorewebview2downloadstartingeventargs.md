---
description: Event args for the `DownloadStarting` event.
title: WebView2 Win32 C++ ICoreWebView2DownloadStartingEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DownloadStartingEventArgs
---

# interface ICoreWebView2DownloadStartingEventArgs

```
interface ICoreWebView2DownloadStartingEventArgs
  : public IUnknown
```

Event args for the `DownloadStarting` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | The host may set this flag to cancel the download.
[get_DownloadOperation](#get_downloadoperation) | Returns the ICoreWebView2DownloadOperation for the download that has started.
[get_Handled](#get_handled) | The host may set this flag to `TRUE` to hide the default download dialog for this download.
[get_ResultFilePath](#get_resultfilepath) | The path to the file.
[GetDeferral](#getdeferral) | Returns an ICoreWebView2Deferral object.
[put_Cancel](#put_cancel) | Sets the `Cancel` property.
[put_Handled](#put_handled) | Sets the `Handled` property.
[put_ResultFilePath](#put_resultfilepath) | Sets the `ResultFilePath` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.902.49
WebView2 Win32 Prerelease |    1.0.902

## Members

#### get_Cancel

The host may set this flag to cancel the download.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * cancel)

If canceled, the download save dialog is not displayed regardless of the `Handled` property.

#### get_DownloadOperation

Returns the ICoreWebView2DownloadOperation for the download that has started.

> public HRESULT [get_DownloadOperation](#get_downloadoperation)(ICoreWebView2DownloadOperation ** downloadOperation)

#### get_Handled

The host may set this flag to `TRUE` to hide the default download dialog for this download.

> public HRESULT [get_Handled](#get_handled)(BOOL * handled)

The download will progress as normal if it is not canceled, there will just be no default UI shown. By default the value is `FALSE` and the default download dialog is shown.

#### get_ResultFilePath

The path to the file.

> public HRESULT [get_ResultFilePath](#get_resultfilepath)(LPWSTR * resultFilePath)

If setting the path, the host should ensure that it is an absolute path, including the file name, and that the path does not point to an existing file. If the path points to an existing file, the file will be overwritten. If the directory does not exist, it is created.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### GetDeferral

Returns an ICoreWebView2Deferral object.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use this operation to complete the event at a later time.

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL cancel)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL handled)

#### put_ResultFilePath

Sets the `ResultFilePath` property.

> public HRESULT [put_ResultFilePath](#put_resultfilepath)(LPCWSTR resultFilePath)

