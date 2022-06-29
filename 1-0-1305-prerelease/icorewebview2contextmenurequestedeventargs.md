---
description: Event args for the `ContextMenuRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ContextMenuRequestedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuRequestedEventArgs
---

# interface ICoreWebView2ContextMenuRequestedEventArgs

```
interface ICoreWebView2ContextMenuRequestedEventArgs
  : public IUnknown
```

Event args for the `ContextMenuRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ContextMenuTarget](#get_contextmenutarget) | Gets the target information associated with the requested context menu.
[get_Handled](#get_handled) | Gets whether the `ContextMenuRequested` event is handled by host.
[get_Location](#get_location) | Gets the coordinates where the context menu request occurred in relation to the upper left corner of the WebView bounds.
[get_MenuItems](#get_menuitems) | Gets the collection of `ContextMenuItem` objects.
[get_SelectedCommandId](#get_selectedcommandid) | Gets the selected CommandId.
[GetDeferral](#getdeferral) | Returns an ICoreWebView2Deferral object.
[put_Handled](#put_handled) | Sets whether the `ContextMenuRequested` event is handled by host after the event handler completes or if there is a deferral then after the deferral is completed.
[put_SelectedCommandId](#put_selectedcommandid) | Sets the selected context menu item's command ID.

Will contain the selection information and a collection of all of the default context menu items that the WebView would show. Allows the app to draw its own context menu or add/remove from the default context menu.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_ContextMenuTarget

Gets the target information associated with the requested context menu.

> public HRESULT [get_ContextMenuTarget](#get_contextmenutarget)(ICoreWebView2ContextMenuTarget ** value)

See ICoreWebView2ContextMenuTarget for more details.

#### get_Handled

Gets whether the `ContextMenuRequested` event is handled by host.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Location

Gets the coordinates where the context menu request occurred in relation to the upper left corner of the WebView bounds.

> public HRESULT [get_Location](#get_location)(POINT * value)

#### get_MenuItems

Gets the collection of `ContextMenuItem` objects.

> public HRESULT [get_MenuItems](#get_menuitems)(ICoreWebView2ContextMenuItemCollection ** value)

See ICoreWebView2ContextMenuItemCollection for more details.

#### get_SelectedCommandId

Gets the selected CommandId.

> public HRESULT [get_SelectedCommandId](#get_selectedcommandid)(INT32 * value)

#### GetDeferral

Returns an ICoreWebView2Deferral object.

> public HRESULT [GetDeferral](#getdeferral)(ICoreWebView2Deferral ** deferral)

Use this operation to complete the event when the custom context menu is closed.

#### put_Handled

Sets whether the `ContextMenuRequested` event is handled by host after the event handler completes or if there is a deferral then after the deferral is completed.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

If `Handled` is set to TRUE then WebView will not display a context menu and will instead use the `SelectedCommandId` property to indicate which, if any, context menu item command to invoke. If after the event handler or deferral completes `Handled` is set to FALSE then WebView will display a context menu based on the contents of the `MenuItems` property. The default value is FALSE.

#### put_SelectedCommandId

Sets the selected context menu item's command ID.

> public HRESULT [put_SelectedCommandId](#put_selectedcommandid)(INT32 value)

When this is set, WebView will execute the selected command. This value should always be obtained via the selected `ContextMenuItem`'s `CommandId` property. The default value is -1 which means that no selection occurred. The app can also report the selected command ID for a custom context menu item, which will cause the `CustomItemSelected` event to be fired for the custom item, however while command IDs for each custom context menu item is unique during a ContextMenuRequested event, CoreWebView2 may reassign command ID values of deleted custom ContextMenuItems to new objects and the command ID assigned to the same custom item can be different between each app runtime.

