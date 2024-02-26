---
description: Provides a set of properties for managing an Extension, which includes an ID, name, and whether it is enabled or not, and the ability to Remove the Extension, and enable or disable it.
title: WebView2 Win32 C++ ICoreWebView2BrowserExtension
ms.date: 02/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2BrowserExtension
topic_type: 
- APIRef
api_name:
- ICoreWebView2BrowserExtension
- ICoreWebView2BrowserExtension.Enable
- ICoreWebView2BrowserExtension.get_Id
- ICoreWebView2BrowserExtension.get_IsEnabled
- ICoreWebView2BrowserExtension.get_Name
- ICoreWebView2BrowserExtension.Remove
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2BrowserExtension

```
interface ICoreWebView2BrowserExtension
  : public IUnknown
```

Provides a set of properties for managing an Extension, which includes an ID, name, and whether it is enabled or not, and the ability to Remove the Extension, and enable or disable it.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Enable](#enable) | Sets whether this browser extension is enabled or disabled.
[get_Id](#get_id) | This is the browser extension's ID.
[get_IsEnabled](#get_isenabled) | If `isEnabled` is true then the Extension is enabled and running in WebView instances.
[get_Name](#get_name) | This is the browser extension's name.
[Remove](#remove) | Removes this browser extension from its WebView2 Profile.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Enable

Sets whether this browser extension is enabled or disabled.

> public HRESULT [Enable](#enable)(BOOL isEnabled, ICoreWebView2BrowserExtensionEnableCompletedHandler * handler)

This change applies immediately to the extension in all HTML documents in all WebView2s associated with this profile. After an extension is removed, calling `Enable` will not change the value of `IsEnabled`.

#### get_Id

This is the browser extension's ID.

> public HRESULT [get_Id](#get_id)(LPWSTR * value)

This is the same browser extension ID returned by the browser extension API [`chrome.runtime.id`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/runtime/id). Please see that documentation for more details on how the ID is generated. After an extension is removed, calling `Id` will return the id of the extension that is removed. The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_IsEnabled

If `isEnabled` is true then the Extension is enabled and running in WebView instances.

> public HRESULT [get_IsEnabled](#get_isenabled)(BOOL * value)

If it is false then the Extension is disabled and not running in WebView instances. When a Extension is first installed, `IsEnable` are default to be `TRUE`. `isEnabled` is persisted per profile. After an extension is removed, calling `isEnabled` will return the value at the time it was removed.

#### get_Name

This is the browser extension's name.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

This value is defined in this browser extension's manifest.json file. If manifest.json define extension's localized name, this value will be the localized version of the name. Please see [Manifest.json name](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/name) for more details. After an extension is removed, calling `Name` will return the name of the extension that is removed. The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### Remove

Removes this browser extension from its WebView2 Profile.

> public HRESULT [Remove](#remove)(ICoreWebView2BrowserExtensionRemoveCompletedHandler * handler)

The browser extension is removed immediately including from all currently running HTML documents associated with this WebView2 Profile. The removal is persisted and future uses of this profile will not have this extension installed. After an extension is removed, calling `Remove` again will cause an exception.

