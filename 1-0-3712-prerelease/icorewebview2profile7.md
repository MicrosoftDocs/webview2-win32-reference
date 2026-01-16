---
description: Interfaces in profile for managing browser extensions.
title: WebView2 Win32 C++ ICoreWebView2Profile7
ms.date: 12/02/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile7
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile7
- ICoreWebView2Profile7.AddBrowserExtension
- ICoreWebView2Profile7.GetBrowserExtensions
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile7

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Profile7
  : public ICoreWebView2Profile6
```

Interfaces in profile for managing browser extensions.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AddBrowserExtension](#addbrowserextension) | Adds the [browser extension](https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions) using the extension path for unpacked extensions from the local device.
[GetBrowserExtensions](#getbrowserextensions) | Gets a snapshot of the set of extensions installed at the time `GetBrowserExtensions` is called.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### AddBrowserExtension

Adds the [browser extension](https://developer.mozilla.org/docs/Mozilla/Add-ons/WebExtensions) using the extension path for unpacked extensions from the local device.

> public HRESULT [AddBrowserExtension](#addbrowserextension)(LPCWSTR extensionFolderPath, [ICoreWebView2ProfileAddBrowserExtensionCompletedHandler](icorewebview2profileaddbrowserextensioncompletedhandler.md#icorewebview2profileaddbrowserextensioncompletedhandler) * handler)

Extension is running right after installation. The extension folder path is the topmost folder of an unpacked browser extension and contains the browser extension manifest file. If the `extensionFolderPath` is an invalid path or doesn't contain the extension manifest.json file, this function will return `ERROR_FILE_NOT_FOUND` to callers. Installed extension will default `IsEnabled` to true. When `AreBrowserExtensionsEnabled` is `FALSE`, `AddBrowserExtension` will fail and return HRESULT `ERROR_NOT_SUPPORTED`. During installation, the content of the extension is not copied to the user data folder. Once the extension is installed, changing the content of the extension will cause the extension to be removed from the installed profile. When an extension is added the extension is persisted in the corresponding profile. The extension will still be installed the next time you use this profile. When an extension is installed from a folder path, adding the same extension from the same folder path means reinstalling this extension. When two extensions with the same Id are installed, only the later installed extension will be kept.

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

> public HRESULT [GetBrowserExtensions](#getbrowserextensions)([ICoreWebView2ProfileGetBrowserExtensionsCompletedHandler](icorewebview2profilegetbrowserextensionscompletedhandler.md#icorewebview2profilegetbrowserextensionscompletedhandler) * handler)

If an extension is installed or uninstalled after `GetBrowserExtensions` completes, the list returned by `GetBrowserExtensions` remains the same. When `AreBrowserExtensionsEnabled` is `FALSE`, `GetBrowserExtensions` won't return any extensions on current user profile.

