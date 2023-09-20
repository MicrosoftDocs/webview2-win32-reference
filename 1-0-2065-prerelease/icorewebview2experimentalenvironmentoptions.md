---
description: Additional options used to create WebView2 Environment.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironmentOptions
ms.date: 09/20/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironmentOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironmentOptions
- ICoreWebView2ExperimentalEnvironmentOptions.get_AreBrowserExtensionsEnabled
- ICoreWebView2ExperimentalEnvironmentOptions.put_AreBrowserExtensionsEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironmentOptions

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironmentOptions
  : public IUnknown
```

Additional options used to create WebView2 Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreBrowserExtensionsEnabled](#get_arebrowserextensionsenabled) | When `AreBrowserExtensionsEnabled` is set to `TRUE`, new extensions can be added to user profile and used.
[put_AreBrowserExtensionsEnabled](#put_arebrowserextensionsenabled) | Sets the `AreBrowserExtensionsEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.579

## Members

#### get_AreBrowserExtensionsEnabled

When `AreBrowserExtensionsEnabled` is set to `TRUE`, new extensions can be added to user profile and used.

> public HRESULT [get_AreBrowserExtensionsEnabled](#get_arebrowserextensionsenabled)(BOOL * value)

`AreBrowserExtensionsEnabled` is default to be `FALSE`, in this case, new extensions can't be installed, and already installed extension won't be available to use in user profile. If connecting to an already running environment with a different value for `AreBrowserExtensionsEnabled` property, it will fail with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`. See `ICoreWebView2BrowserExtension` for Extensions API details.

#### put_AreBrowserExtensionsEnabled

Sets the `AreBrowserExtensionsEnabled` property.

> public HRESULT [put_AreBrowserExtensionsEnabled](#put_arebrowserextensionsenabled)(BOOL value)

