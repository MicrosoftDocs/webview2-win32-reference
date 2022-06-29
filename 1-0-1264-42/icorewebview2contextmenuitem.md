---
description: Represents a context menu item of a context menu displayed by WebView.
title: WebView2 Win32 C++ ICoreWebView2ContextMenuItem
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuItem
---

# interface ICoreWebView2ContextMenuItem

```
interface ICoreWebView2ContextMenuItem
  : public IUnknown
```

Represents a context menu item of a context menu displayed by WebView.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_CustomItemSelected](#add_customitemselected) | Add an event handler for the `CustomItemSelected` event.
[get_Children](#get_children) | Gets the list of children menu items through a `ContextMenuItemCollection` if the kind is Submenu.
[get_CommandId](#get_commandid) | Gets the Command ID for the `ContextMenuItem`.
[get_Icon](#get_icon) | Gets the Icon for the `ContextMenuItem` in PNG, Bitmap or SVG formats in the form of an IStream.
[get_IsChecked](#get_ischecked) | Gets the checked property of the `ContextMenuItem`, used if the kind is Check box or Radio.
[get_IsEnabled](#get_isenabled) | Gets the enabled property of the `ContextMenuItem`.
[get_Kind](#get_kind) | Gets the `ContextMenuItem` kind.
[get_Label](#get_label) | Gets the localized label for the `ContextMenuItem`.
[get_Name](#get_name) | Gets the unlocalized name for the `ContextMenuItem`.
[get_ShortcutKeyDescription](#get_shortcutkeydescription) | Gets the localized keyboard shortcut for this ContextMenuItem.
[put_IsChecked](#put_ischecked) | Sets the checked property of the `ContextMenuItem`.
[put_IsEnabled](#put_isenabled) | Sets the enabled property of the `ContextMenuItem`.
[remove_CustomItemSelected](#remove_customitemselected) | Remove an event handler previously added with `add_CustomItemSelected`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### add_CustomItemSelected

Add an event handler for the `CustomItemSelected` event.

> public HRESULT [add_CustomItemSelected](#add_customitemselected)([ICoreWebView2CustomItemSelectedEventHandler](icorewebview2customitemselectedeventhandler.md) * eventHandler, EventRegistrationToken * token)

`CustomItemSelected` event is raised when the user selects this `ContextMenuItem`. Will only be raised for end developer created context menu items

#### get_Children

Gets the list of children menu items through a `ContextMenuItemCollection` if the kind is Submenu.

> public HRESULT [get_Children](#get_children)([ICoreWebView2ContextMenuItemCollection](icorewebview2contextmenuitemcollection.md) ** value)

If the kind is not submenu, will return null.

#### get_CommandId

Gets the Command ID for the `ContextMenuItem`.

> public HRESULT [get_CommandId](#get_commandid)(INT32 * value)

Use this to report the `SelectedCommandId` in `ContextMenuRequested` event.

#### get_Icon

Gets the Icon for the `ContextMenuItem` in PNG, Bitmap or SVG formats in the form of an IStream.

> public HRESULT [get_Icon](#get_icon)(IStream ** value)

Stream will be rewound to the start of the image data.

#### get_IsChecked

Gets the checked property of the `ContextMenuItem`, used if the kind is Check box or Radio.

> public HRESULT [get_IsChecked](#get_ischecked)(BOOL * value)

#### get_IsEnabled

Gets the enabled property of the `ContextMenuItem`.

> public HRESULT [get_IsEnabled](#get_isenabled)(BOOL * value)

#### get_Kind

Gets the `ContextMenuItem` kind.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND * value)

#### get_Label

Gets the localized label for the `ContextMenuItem`.

> public HRESULT [get_Label](#get_label)(LPWSTR * value)

Will contain an ampersand for characters to be used as keyboard accelerator.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_Name

Gets the unlocalized name for the `ContextMenuItem`.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

Use this to distinguish between context menu item types. This will be the English label of the menu item in lower camel case. For example, the "Save as" menu item will be "saveAs". Extension menu items will be "extension", custom menu items will be "custom" and spellcheck items will be "spellCheck". Some example context menu item names are:

* "saveAs"

* "copyImage"

* "openLinkInNewWindow"

* "cut"

* "copy"

* "paste"

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ShortcutKeyDescription

Gets the localized keyboard shortcut for this ContextMenuItem.

> public HRESULT [get_ShortcutKeyDescription](#get_shortcutkeydescription)(LPWSTR * value)

It will be the empty string if there is no keyboard shortcut. This is text intended to be displayed to the end user to show the keyboard shortcut. For example this property is Ctrl+Shift+I for the "Inspect" `ContextMenuItem`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_IsChecked

Sets the checked property of the `ContextMenuItem`.

> public HRESULT [put_IsChecked](#put_ischecked)(BOOL value)

Must only be used for custom context menu items that are of kind Check box or Radio.

#### put_IsEnabled

Sets the enabled property of the `ContextMenuItem`.

> public HRESULT [put_IsEnabled](#put_isenabled)(BOOL value)

Must only be used in the case of a custom context menu item. The default value for this is `TRUE`.

#### remove_CustomItemSelected

Remove an event handler previously added with `add_CustomItemSelected`.

> public HRESULT [remove_CustomItemSelected](#remove_customitemselected)(EventRegistrationToken token)

