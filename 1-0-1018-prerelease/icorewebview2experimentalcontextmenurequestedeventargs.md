---
description: Event args for the `ContextMenuRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalContextMenuRequestedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 09/20/2021
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalContextMenuRequestedEventArgs
---

# interface ICoreWebView2ExperimentalContextMenuRequestedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalContextMenuRequestedEventArgs
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
[GetDeferral](#getdeferral) | Returns an [ICoreWebView2Deferral](icorewebview2deferral.md) object.
[put_Handled](#put_handled) | Sets whether the `ContextMenuRequested` event is handled by host after the event handler completes or if there is a deferral then after the deferral is completed.
[put_SelectedCommandId](#put_selectedcommandid) | Sets the selected command for the WebView to execute.

Will contain the selection information and a collection of all of the default context menu items that the WebView would show. Allows the app to draw its own context menu or add/remove from the default context menu.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_ContextMenuTarget

Gets the target information associated with the requested context menu.

> public HRESULT [get_ContextMenuTarget](#get_contextmenutarget)([ICoreWebView2ExperimentalContextMenuTarget](icorewebview2experimentalcontextmenutarget.md) ** value)

See `ICoreWebView2ContextMenuTarget` for more details.

#### get_Handled

Gets whether the `ContextMenuRequested` event is handled by host.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Location

Gets the coordinates where the context menu request occurred in relation to the upper left corner of the WebView bounds.

> public HRESULT [get_Location](#get_location)(POINT * value)

#### get_MenuItems

Gets the collection of `ContextMenuItem` objects.

> public HRESULT [get_MenuItems](#get_menuitems)([ICoreWebView2ExperimentalContextMenuItemCollection](icorewebview2experimentalcontextmenuitemcollection.md) ** value)

See `ICoreWebView2ContextMenuItemCollection` for more details.

#### get_SelectedCommandId

Gets the selected CommandId.

> public HRESULT [get_SelectedCommandId](#get_selectedcommandid)(INT32 * value)

#### GetDeferral

Returns an [ICoreWebView2Deferral](icorewebview2deferral.md) object.

> public HRESULT [GetDeferral](#getdeferral)([ICoreWebView2Deferral](icorewebview2deferral.md) ** deferral)

Use this operation to complete the event when the custom context menu is closed.

#### put_Handled

Sets whether the `ContextMenuRequested` event is handled by host after the event handler completes or if there is a deferral then after the deferral is completed.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

If `Handled` is set to TRUE then WebView will not display a context menu and will instead use the `SelectedCommandId` property to indicate which, if any, context menu item to invoke. If after the event handler or deferral completes `Handled` is set to FALSE then WebView will display a context menu based on the contents of the `MenuItems` property. The default value is FALSE.

#### put_SelectedCommandId

Sets the selected command for the WebView to execute.

> public HRESULT [put_SelectedCommandId](#put_selectedcommandid)(INT32 value)

The value is obtained via the `ContextMenuItem` CommandId property. This value should always be from context menu items for the relevant context menu and event arg. Attempting to mix will result in invalid outputs. The default value is -1 which means that no selected occurred.

