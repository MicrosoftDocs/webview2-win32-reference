---
description: Represents a collection of `ContextMenuItem` objects.
title: WebView2 Win32 C++ ICoreWebView2ContextMenuItemCollection
ms.date: 01/16/2025
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ContextMenuItemCollection
  : public IUnknown
```

Represents a collection of `ContextMenuItem` objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Count](#get_count) | Gets the number of `ContextMenuItem` objects contained in the `ContextMenuItemCollection`.
[GetValueAtIndex](#getvalueatindex) | Gets the `ContextMenuItem` at the specified index.
[InsertValueAtIndex](#insertvalueatindex) | Inserts the `ContextMenuItem` at the specified index.
[RemoveValueAtIndex](#removevalueatindex) | Removes the `ContextMenuItem` at the specified index.

Used to get, remove and add `ContextMenuItem` objects at the specified index.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_Count

Gets the number of `ContextMenuItem` objects contained in the `ContextMenuItemCollection`.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the `ContextMenuItem` at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) ** value)

#### InsertValueAtIndex

Inserts the `ContextMenuItem` at the specified index.

> public HRESULT [InsertValueAtIndex](#insertvalueatindex)(UINT32 index, [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md#icorewebview2contextmenuitem) * value)

#### RemoveValueAtIndex

Removes the `ContextMenuItem` at the specified index.

> public HRESULT [RemoveValueAtIndex](#removevalueatindex)(UINT32 index)

