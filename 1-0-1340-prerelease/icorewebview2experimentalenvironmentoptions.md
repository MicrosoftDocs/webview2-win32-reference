---
description: This is the ICoreWebView2ExperimentalEnvironmentOptions interface.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironmentOptions
ms.date: 09/06/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironmentOptions
---

# interface ICoreWebView2ExperimentalEnvironmentOptions

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironmentOptions
  : public IUnknown
```

This is the ICoreWebView2ExperimentalEnvironmentOptions interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[GetCustomSchemeRegistrations](#getcustomschemeregistrations) | Array of custom scheme registrations.
[SetCustomSchemeRegistrations](#setcustomschemeregistrations) | Set the array of custom scheme registrations to be used.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.579

## Members

#### GetCustomSchemeRegistrations

Array of custom scheme registrations.

> public HRESULT [GetCustomSchemeRegistrations](#getcustomschemeregistrations)(UINT32 * count, [ICoreWebView2ExperimentalCustomSchemeRegistration](icorewebview2experimentalcustomschemeregistration.md) *** schemeRegistrations)

The returned ICoreWebView2CustomSchemeRegistration pointers must be released, and the array itself must be deallocated with CoTaskMemFree.

#### SetCustomSchemeRegistrations

Set the array of custom scheme registrations to be used.

> public HRESULT [SetCustomSchemeRegistrations](#setcustomschemeregistrations)(UINT32 count, [ICoreWebView2ExperimentalCustomSchemeRegistration](icorewebview2experimentalcustomschemeregistration.md) ** schemeRegistrations)

