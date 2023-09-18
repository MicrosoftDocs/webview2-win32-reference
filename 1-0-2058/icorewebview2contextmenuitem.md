---
description: 
title: WebView2 Win32 C++ ICoreWebView2ContextMenuItem
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuItem
topic_type: 
- APIRef
api_name:
- ICoreWebView2ContextMenuItem
- ICoreWebView2ContextMenuItem.add_CustomItemSelected
- ICoreWebView2ContextMenuItem.get_Children
- ICoreWebView2ContextMenuItem.get_CommandId
- ICoreWebView2ContextMenuItem.get_Icon
- ICoreWebView2ContextMenuItem.get_IsChecked
- ICoreWebView2ContextMenuItem.get_IsEnabled
- ICoreWebView2ContextMenuItem.get_Kind
- ICoreWebView2ContextMenuItem.get_Label
- ICoreWebView2ContextMenuItem.get_Name
- ICoreWebView2ContextMenuItem.get_ShortcutKeyDescription
- ICoreWebView2ContextMenuItem.put_IsChecked
- ICoreWebView2ContextMenuItem.put_IsEnabled
- ICoreWebView2ContextMenuItem.remove_CustomItemSelected
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ContextMenuItem

```
interface ICoreWebView2ContextMenuItem
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_CustomItemSelected](#add_customitemselected) | Adds an event handler for the `CustomItemSelected` event.
[get_Children](#get_children) | Gets the `Children` property.
[get_CommandId](#get_commandid) | Gets the `CommandId` property.
[get_Icon](#get_icon) | Gets the `Icon` property.
[get_IsChecked](#get_ischecked) | Gets the `IsChecked` property.
[get_IsEnabled](#get_isenabled) | Gets the `IsEnabled` property.
[get_Kind](#get_kind) | Gets the `Kind` property.
[get_Label](#get_label) | Gets the `Label` property.
[get_Name](#get_name) | Gets the `Name` property.
[get_ShortcutKeyDescription](#get_shortcutkeydescription) | Gets the `ShortcutKeyDescription` property.
[put_IsChecked](#put_ischecked) | Sets the `IsChecked` property.
[put_IsEnabled](#put_isenabled) | Sets the `IsEnabled` property.
[remove_CustomItemSelected](#remove_customitemselected) | Removes an event handler previously added with `add_CustomItemSelected`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### add_CustomItemSelected

Adds an event handler for the `CustomItemSelected` event.

> public HRESULT [add_CustomItemSelected](#add_customitemselected)([ICoreWebView2CustomItemSelectedEventHandler](icorewebview2customitemselectedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_Children

Gets the `Children` property.

> public HRESULT [get_Children](#get_children)(ICoreWebView2ContextMenuItemCollection ** value)

#### get_CommandId

Gets the `CommandId` property.

> public HRESULT [get_CommandId](#get_commandid)(INT32 * value)

#### get_Icon

Gets the `Icon` property.

> public HRESULT [get_Icon](#get_icon)(IStream ** value)

#### get_IsChecked

Gets the `IsChecked` property.

> public HRESULT [get_IsChecked](#get_ischecked)(BOOL * value)

#### get_IsEnabled

Gets the `IsEnabled` property.

> public HRESULT [get_IsEnabled](#get_isenabled)(BOOL * value)

#### get_Kind

Gets the `Kind` property.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND * value)

#### get_Label

Gets the `Label` property.

> public HRESULT [get_Label](#get_label)(LPWSTR * value)

#### get_Name

Gets the `Name` property.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

#### get_ShortcutKeyDescription

Gets the `ShortcutKeyDescription` property.

> public HRESULT [get_ShortcutKeyDescription](#get_shortcutkeydescription)(LPWSTR * value)

#### put_IsChecked

Sets the `IsChecked` property.

> public HRESULT [put_IsChecked](#put_ischecked)(BOOL value)

#### put_IsEnabled

Sets the `IsEnabled` property.

> public HRESULT [put_IsEnabled](#put_isenabled)(BOOL value)

#### remove_CustomItemSelected

Removes an event handler previously added with `add_CustomItemSelected`.

> public HRESULT [remove_CustomItemSelected](#remove_customitemselected)(EventRegistrationToken token)

