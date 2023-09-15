---
description: 
title: WebView2 Win32 C++ ICoreWebView2NewWindowRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NewWindowRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2NewWindowRequestedEventArgs
- ICoreWebView2NewWindowRequestedEventArgs.get_Handled
- ICoreWebView2NewWindowRequestedEventArgs.get_IsUserInitiated
- ICoreWebView2NewWindowRequestedEventArgs.get_NewWindow
- ICoreWebView2NewWindowRequestedEventArgs.get_Uri
- ICoreWebView2NewWindowRequestedEventArgs.get_WindowFeatures
- ICoreWebView2NewWindowRequestedEventArgs.GetDeferral
- ICoreWebView2NewWindowRequestedEventArgs.put_Handled
- ICoreWebView2NewWindowRequestedEventArgs.put_NewWindow
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NewWindowRequestedEventArgs

```
interface ICoreWebView2NewWindowRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_IsUserInitiated](#get_isuserinitiated) | Gets the `IsUserInitiated` property.
[get_NewWindow](#get_newwindow) | Gets the `NewWindow` property.
[get_Uri](#get_uri) | Gets the `Uri` property.
[get_WindowFeatures](#get_windowfeatures) | Gets the `WindowFeatures` property.
[GetDeferral](#getdeferral) | 
[put_Handled](#put_handled) | Sets the `Handled` property.
[put_NewWindow](#put_newwindow) | Sets the `NewWindow` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_IsUserInitiated

Gets the `IsUserInitiated` property.

> public HRESULT [get_IsUserInitiated](#get_isuserinitiated)(BOOL * value)

#### get_NewWindow

Gets the `NewWindow` property.

> public HRESULT [get_NewWindow](#get_newwindow)([ICoreWebView2](icorewebview2.md) ** value)

#### get_Uri

Gets the `Uri` property.

> public HRESULT [get_Uri](#get_uri)(LPWSTR * value)

#### get_WindowFeatures

Gets the `WindowFeatures` property.

> public HRESULT [get_WindowFeatures](#get_windowfeatures)([ICoreWebView2WindowFeatures](icorewebview2windowfeatures.md) ** value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

#### put_NewWindow

Sets the `NewWindow` property.

> public HRESULT [put_NewWindow](#put_newwindow)([ICoreWebView2](icorewebview2.md) * value)

