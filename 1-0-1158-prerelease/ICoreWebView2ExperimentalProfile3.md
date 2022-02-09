---
description: Experimental Profile interface for DefaultDownloadFolderPath.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile3
ms.date: 02/08/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile3
---

# interface ICoreWebView2ExperimentalProfile3

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile3
  : public IUnknown
```

Experimental Profile interface for DefaultDownloadFolderPath.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_DefaultDownloadFolderPath](#get_defaultdownloadfolderpath) | Gets the `DefaultDownloadFolderPath` property.
[put_DefaultDownloadFolderPath](#put_defaultdownloadfolderpath) | Sets the `DefaultDownloadFolderPath` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_DefaultDownloadFolderPath

Gets the `DefaultDownloadFolderPath` property.

> public HRESULT [get_DefaultDownloadFolderPath](#get_defaultdownloadfolderpath)(LPWSTR * value)

The default value is the system default download folder path for the user.

#### put_DefaultDownloadFolderPath

Sets the `DefaultDownloadFolderPath` property.

> public HRESULT [put_DefaultDownloadFolderPath](#put_defaultdownloadfolderpath)(LPCWSTR value)

The default download folder path is persisted in the user data folder across sessions. The value should be an absolute path to a folder that the user and application can write to. Returns `E_INVALIDARG` if the value is invalid, and the default download folder path is not changed. Otherwise the path is changed immediately. If the directory does not yet exist, it is created at the time of the next download. If the host application does not have permission to create the directory, then the user is prompted to provide a new path through the Save As dialog. The user can override the default download folder path for a given download by choosing a different path in the Save As dialog.

