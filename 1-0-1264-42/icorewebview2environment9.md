---
description: A continuation of the ICoreWebView2Environment interface for creating CoreWebView2 ContextMenuItem objects.
title: WebView2 Win32 C++ ICoreWebView2Environment9
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment9
---

# interface ICoreWebView2Environment9

```
interface ICoreWebView2Environment9
  : public ICoreWebView2Environment8
```

A continuation of the [ICoreWebView2Environment](icorewebview2environment.md) interface for creating CoreWebView2 ContextMenuItem objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateContextMenuItem](#createcontextmenuitem) | Create a custom `ContextMenuItem` object to insert into the WebView context menu.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### CreateContextMenuItem

Create a custom `ContextMenuItem` object to insert into the WebView context menu.

> public HRESULT [CreateContextMenuItem](#createcontextmenuitem)(LPCWSTR label, IStream * iconStream, COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND kind, [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md) ** item)

CoreWebView2 will rewind the icon stream before decoding. There is a limit of 1000 active custom context menu items at a given time. Attempting to create more before deleting existing ones will fail with ERROR_NOT_ENOUGH_QUOTA. It is recommended to reuse ContextMenuItems across ContextMenuRequested events for performance. The returned ContextMenuItem object's `IsEnabled` property will default to `TRUE` and `IsChecked` property will default to `FALSE`. A `CommandId` will be assigned to the ContextMenuItem object that's unique across active custom context menu items, but command ID values of deleted ContextMenuItems can be reassigned.

