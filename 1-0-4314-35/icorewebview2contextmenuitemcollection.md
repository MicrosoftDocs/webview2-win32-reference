---
description: Represents a collection of ICoreWebView2ContextMenuItem objects.
title: WebView2 Win32 C++ ICoreWebView2ContextMenuItemCollection
ms.date: 10-29-2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuItemCollection
topic_type: 
- APIRef
api_name:
- ICoreWebView2ContextMenuItemCollection
- ICoreWebView2ContextMenuItemCollection.get_Count
- ICoreWebView2ContextMenuItemCollection.GetValueAtIndex
- ICoreWebView2ContextMenuItemCollection.InsertValueAtIndex
- ICoreWebView2ContextMenuItemCollection.RemoveValueAtIndex
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ContextMenuItemCollection

```
interface ICoreWebView2ContextMenuItemCollection
  : public IUnknown
```

Represents a collection of [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | Gets the number of [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) objects contained in the ICoreWebView2ContextMenuItemCollection.
[GetValueAtIndex](#getvalueatindex) | Gets the [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) at the specified index.
[InsertValueAtIndex](#insertvalueatindex) | Inserts the [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) at the specified index.
[RemoveValueAtIndex](#removevalueatindex) | Removes the [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) at the specified index.

Used to get, remove and add [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) objects at the specified index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_Count

Gets the number of [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) objects contained in the ICoreWebView2ContextMenuItemCollection.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) ** value)

#### InsertValueAtIndex

Inserts the [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) at the specified index.

> public HRESULT [InsertValueAtIndex](#insertvalueatindex)(UINT32 index, [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) * value)

#### RemoveValueAtIndex

Removes the [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) at the specified index.

> public HRESULT [RemoveValueAtIndex](#removevalueatindex)(UINT32 index)

