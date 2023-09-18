---
description: 
title: WebView2 Win32 C++ ICoreWebView2ContextMenuRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ContextMenuRequestedEventArgs
- ICoreWebView2ContextMenuRequestedEventArgs.get_ContextMenuTarget
- ICoreWebView2ContextMenuRequestedEventArgs.get_Handled
- ICoreWebView2ContextMenuRequestedEventArgs.get_Location
- ICoreWebView2ContextMenuRequestedEventArgs.get_MenuItems
- ICoreWebView2ContextMenuRequestedEventArgs.get_SelectedCommandId
- ICoreWebView2ContextMenuRequestedEventArgs.GetDeferral
- ICoreWebView2ContextMenuRequestedEventArgs.put_Handled
- ICoreWebView2ContextMenuRequestedEventArgs.put_SelectedCommandId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ContextMenuRequestedEventArgs

```
interface ICoreWebView2ContextMenuRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ContextMenuTarget](#get_contextmenutarget) | Gets the `ContextMenuTarget` property.
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_Location](#get_location) | Gets the `Location` property.
[get_MenuItems](#get_menuitems) | Gets the `MenuItems` property.
[get_SelectedCommandId](#get_selectedcommandid) | Gets the `SelectedCommandId` property.
[GetDeferral](#getdeferral) | 
[put_Handled](#put_handled) | Sets the `Handled` property.
[put_SelectedCommandId](#put_selectedcommandid) | Sets the `SelectedCommandId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_ContextMenuTarget

Gets the `ContextMenuTarget` property.

> public HRESULT [get_ContextMenuTarget](#get_contextmenutarget)([ICoreWebView2ContextMenuTarget](icorewebview2contextmenutarget.md) ** value)

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Location

Gets the `Location` property.

> public HRESULT [get_Location](#get_location)(POINT * value)

#### get_MenuItems

Gets the `MenuItems` property.

> public HRESULT [get_MenuItems](#get_menuitems)(ICoreWebView2ContextMenuItemCollection ** value)

#### get_SelectedCommandId

Gets the `SelectedCommandId` property.

> public HRESULT [get_SelectedCommandId](#get_selectedcommandid)(INT32 * value)

#### GetDeferral

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

#### put_SelectedCommandId

Sets the `SelectedCommandId` property.

> public HRESULT [put_SelectedCommandId](#put_selectedcommandid)(INT32 value)

