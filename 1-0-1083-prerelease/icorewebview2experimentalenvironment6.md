---
description: A continuation of the ICoreWebView2ExperimentalEnvironment interface for creating CoreWebView2 ContextMenuItem objects.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment6
ms.date: 11/29/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment6
---

# interface ICoreWebView2ExperimentalEnvironment6

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment6
  : public IUnknown
```

A continuation of the ICoreWebView2ExperimentalEnvironment interface for creating CoreWebView2 ContextMenuItem objects.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateContextMenuItem](#createcontextmenuitem) | Create a `ContextMenuItem` object to insert into the WebView context menu.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### CreateContextMenuItem

Create a `ContextMenuItem` object to insert into the WebView context menu.

> public HRESULT [CreateContextMenuItem](#createcontextmenuitem)(LPCWSTR label, IStream * iconStream, COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND kind, [ICoreWebView2ExperimentalContextMenuItem](icorewebview2experimentalcontextmenuitem.md) ** item)

CoreWebView2 will rewind the icon stream before decoding. Command ID for new custom menu items will be unique for the lifespan of the ContextMenuRequested event. There is a limit of 1000 context menu items that can be created per app runtime. ContextMenuItems are reusable across different ContextMenuRequested events and should be reused for performance reasons and in order not to run over this limit. The specific command ID values may change on each runtime so do not rely on the actual value, but instead use the value given from the object's `get_CommandId` instead. The returned `ContextMenuItem` object's `IsEnabled` property will default to `TRUE` and `IsChecked` property will default to `FALSE`.

