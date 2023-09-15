---
description: 
title: WebView2 Win32 C++ ICoreWebView2DownloadStartingEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DownloadStartingEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2DownloadStartingEventArgs
- ICoreWebView2DownloadStartingEventArgs.get_Cancel
- ICoreWebView2DownloadStartingEventArgs.get_DownloadOperation
- ICoreWebView2DownloadStartingEventArgs.get_Handled
- ICoreWebView2DownloadStartingEventArgs.get_ResultFilePath
- ICoreWebView2DownloadStartingEventArgs.GetDeferral
- ICoreWebView2DownloadStartingEventArgs.put_Cancel
- ICoreWebView2DownloadStartingEventArgs.put_Handled
- ICoreWebView2DownloadStartingEventArgs.put_ResultFilePath
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DownloadStartingEventArgs

```
interface ICoreWebView2DownloadStartingEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Cancel](#get_cancel) | Gets the `Cancel` property.
[get_DownloadOperation](#get_downloadoperation) | Gets the `DownloadOperation` property.
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_ResultFilePath](#get_resultfilepath) | Gets the `ResultFilePath` property.
[GetDeferral](#getdeferral) | 
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

Gets the `Cancel` property.

> public HRESULT [get_Cancel](#get_cancel)(BOOL * value)

#### get_DownloadOperation

Gets the `DownloadOperation` property.

> public HRESULT [get_DownloadOperation](#get_downloadoperation)([ICoreWebView2DownloadOperation](icorewebview2downloadoperation.md) ** value)

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_ResultFilePath

Gets the `ResultFilePath` property.

> public HRESULT [get_ResultFilePath](#get_resultfilepath)(LPWSTR * value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Cancel

Sets the `Cancel` property.

> public HRESULT [put_Cancel](#put_cancel)(BOOL value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

#### put_ResultFilePath

Sets the `ResultFilePath` property.

> public HRESULT [put_ResultFilePath](#put_resultfilepath)(LPCWSTR value)

