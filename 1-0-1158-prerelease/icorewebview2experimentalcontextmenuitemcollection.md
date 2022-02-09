---
description: Represents a collection of `ContextMenuItem` objects.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalContextMenuItemCollection
ms.date: 02/09/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalContextMenuItemCollection
---

# interface ICoreWebView2ExperimentalContextMenuItemCollection

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalContextMenuItemCollection
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_Count

Gets the number of `ContextMenuItem` objects contained in the `ContextMenuItemCollection`.

> public HRESULT [get_Count](#get_count)(UINT32 * value)

#### GetValueAtIndex

Gets the `ContextMenuItem` at the specified index.

> public HRESULT [GetValueAtIndex](#getvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalContextMenuItem](icorewebview2experimentalcontextmenuitem.md) ** value)

#### InsertValueAtIndex

Inserts the `ContextMenuItem` at the specified index.

> public HRESULT [InsertValueAtIndex](#insertvalueatindex)(UINT32 index, [ICoreWebView2ExperimentalContextMenuItem](icorewebview2experimentalcontextmenuitem.md) * value)

#### RemoveValueAtIndex

Removes the `ContextMenuItem` at the specified index.

> public HRESULT [RemoveValueAtIndex](#removevalueatindex)(UINT32 index)

