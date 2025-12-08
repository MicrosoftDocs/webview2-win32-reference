---
description: Additional options used to create WebView2 Environment to manage browser extensions.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions6
ms.date: 12/02/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions6
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions6
- ICoreWebView2EnvironmentOptions6.get_AreBrowserExtensionsEnabled
- ICoreWebView2EnvironmentOptions6.put_AreBrowserExtensionsEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions6

```
interface ICoreWebView2EnvironmentOptions6
  : public IUnknown
```

Additional options used to create WebView2 Environment to manage browser extensions.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AreBrowserExtensionsEnabled](#get_arebrowserextensionsenabled) | Gets the `AreBrowserExtensionsEnabled` property.
[put_AreBrowserExtensionsEnabled](#put_arebrowserextensionsenabled) | When `AreBrowserExtensionsEnabled` is set to `TRUE`, new extensions can be added to user profile and used.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### get_AreBrowserExtensionsEnabled

Gets the `AreBrowserExtensionsEnabled` property.

> public HRESULT [get_AreBrowserExtensionsEnabled](#get_arebrowserextensionsenabled)(BOOL * value)

#### put_AreBrowserExtensionsEnabled

When `AreBrowserExtensionsEnabled` is set to `TRUE`, new extensions can be added to user profile and used.

> public HRESULT [put_AreBrowserExtensionsEnabled](#put_arebrowserextensionsenabled)(BOOL value)

`AreBrowserExtensionsEnabled` is default to be `FALSE`, in this case, new extensions can't be installed, and already installed extension won't be available to use in user profile. If connecting to an already running environment with a different value for `AreBrowserExtensionsEnabled` property, it will fail with `HRESULT_FROM_WIN32(ERROR_INVALID_STATE)`. See [ICoreWebView2BrowserExtension](icorewebview2browserextension.md#icorewebview2browserextension) for Extensions API details.

