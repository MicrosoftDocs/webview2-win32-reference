---
description: Representation of a DOM FileSystemHandle object.
title: WebView2 Win32 C++ ICoreWebView2FileSystemHandle
ms.date: 06/23/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FileSystemHandle
topic_type: 
- APIRef
api_name:
- ICoreWebView2FileSystemHandle
- ICoreWebView2FileSystemHandle.get_Kind
- ICoreWebView2FileSystemHandle.get_Path
- ICoreWebView2FileSystemHandle.get_Permission
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FileSystemHandle

```
interface ICoreWebView2FileSystemHandle
  : public IUnknown
```

Representation of a DOM [FileSystemHandle](https://developer.mozilla.org/docs/Web/API/FileSystemHandle) object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Kind](#get_kind) | The kind of the FileSystemHandle. It can either be a file or a directory.
[get_Path](#get_path) | The path to the FileSystemHandle.
[get_Permission](#get_permission) | The permissions granted to the FileSystemHandle.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2651.64
WebView2 Win32 Prerelease |    1.0.2646

## Members

#### get_Kind

The kind of the FileSystemHandle. It can either be a file or a directory.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_FILE_SYSTEM_HANDLE_KIND * value)

#### get_Path

The path to the FileSystemHandle.

> public HRESULT [get_Path](#get_path)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Permission

The permissions granted to the FileSystemHandle.

> public HRESULT [get_Permission](#get_permission)(COREWEBVIEW2_FILE_SYSTEM_HANDLE_PERMISSION * value)

