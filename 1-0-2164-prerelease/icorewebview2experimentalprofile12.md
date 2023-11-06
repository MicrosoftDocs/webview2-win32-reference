---
description: This is the ICoreWebView2 experimental profile interface that manages browser extensions.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile12
ms.date: 11/06/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile12
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile12
- ICoreWebView2ExperimentalProfile12.AddBrowserExtension
- ICoreWebView2ExperimentalProfile12.GetBrowserExtensions
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile12

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile12
  : public IUnknown
```

This is the [ICoreWebView2](icorewebview2.md) experimental profile interface that manages browser extensions.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AddBrowserExtension](#addbrowserextension) | Adds the [browser extension](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions) using the extension path for unpacked extensions from the local device.
[GetBrowserExtensions](#getbrowserextensions) | Gets a snapshot of the set of extensions installed at the time `GetBrowserExtensions` is called.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1988

## Members

#### AddBrowserExtension

Adds the [browser extension](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions) using the extension path for unpacked extensions from the local device.

> public HRESULT [AddBrowserExtension](#addbrowserextension)(LPCWSTR extensionFolderPath, ICoreWebView2ExperimentalProfileAddBrowserExtensionCompletedHandler * handler)

Extension is running right after installation. The extension folder path is the topmost folder of an unpacked browser extension and contains the browser extension manifest file. If the `extensionFolderPath` is an invalid path or doesn't contain the extension manifest.json file, this function will return `ERROR_FILE_NOT_FOUND` to callers. Installed extension will default `IsEnabled` to true. When `AreBrowserExtensionsEnabled` is `FALSE`, `AddBrowserExtension` will fail and return HRESULT `ERROR_NOT_SUPPORTED`. During installation, the content of the extension is not copied to the user data folder. Once the extension is installed, changing the content of the extension will cause the extension to be removed from the installed profile. When an extension is added the extension is persisted in the corresponding profile. The extension will still be installed the next time you use this profile. When an extension is installed from a folder path, adding the same extension from the same folder path means reinstalleing this extension. When two extensions with the same Id are installed, only the later installed extension will be kept.

Extensions that are designed to include any UI interactions (e.g. icon, badge, pop up, etc.) can be loaded and used but will have missing UI entry points due to the lack of browser UI elements to host these entry points in WebView2.

The following summarizes the possible error values that can be returned from `AddBrowserExtension` and a description of why these errors occur.

Error value   |Description
--------- | ---------
`HRESULT_FROM_WIN32(ERROR_NOT_SUPPORTED)`|Extensions are disabled.
`HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)`|Cannot find `manifest.json` file or it is not a valid extension manifest.
`E_ACCESSDENIED`|Cannot load extension with file or directory name starting with "_", reserved for use by the system.
`E_FAIL`|Extension failed to install with other unknown reasons.

#### GetBrowserExtensions

Gets a snapshot of the set of extensions installed at the time `GetBrowserExtensions` is called.

> public HRESULT [GetBrowserExtensions](#getbrowserextensions)(ICoreWebView2ExperimentalProfileGetBrowserExtensionsCompletedHandler * handler)

If an extension is installed or uninstalled after `GetBrowserExtensions` completes, the list returned by `GetBrowserExtensions` remains the same. When `AreBrowserExtensionsEnabled` is `FALSE`, `GetBrowserExtensions` won't return any extensions on current user profile.

