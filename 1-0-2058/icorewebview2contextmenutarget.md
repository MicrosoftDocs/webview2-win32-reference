---
description: 
title: WebView2 Win32 C++ ICoreWebView2ContextMenuTarget
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ContextMenuTarget
topic_type: 
- APIRef
api_name:
- ICoreWebView2ContextMenuTarget
- ICoreWebView2ContextMenuTarget.get_FrameUri
- ICoreWebView2ContextMenuTarget.get_HasLinkText
- ICoreWebView2ContextMenuTarget.get_HasLinkUri
- ICoreWebView2ContextMenuTarget.get_HasSelection
- ICoreWebView2ContextMenuTarget.get_HasSourceUri
- ICoreWebView2ContextMenuTarget.get_IsEditable
- ICoreWebView2ContextMenuTarget.get_IsRequestedForMainFrame
- ICoreWebView2ContextMenuTarget.get_Kind
- ICoreWebView2ContextMenuTarget.get_LinkText
- ICoreWebView2ContextMenuTarget.get_LinkUri
- ICoreWebView2ContextMenuTarget.get_PageUri
- ICoreWebView2ContextMenuTarget.get_SelectionText
- ICoreWebView2ContextMenuTarget.get_SourceUri
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ContextMenuTarget

```
interface ICoreWebView2ContextMenuTarget
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_FrameUri](#get_frameuri) | Gets the `FrameUri` property.
[get_HasLinkText](#get_haslinktext) | Gets the `HasLinkText` property.
[get_HasLinkUri](#get_haslinkuri) | Gets the `HasLinkUri` property.
[get_HasSelection](#get_hasselection) | Gets the `HasSelection` property.
[get_HasSourceUri](#get_hassourceuri) | Gets the `HasSourceUri` property.
[get_IsEditable](#get_iseditable) | Gets the `IsEditable` property.
[get_IsRequestedForMainFrame](#get_isrequestedformainframe) | Gets the `IsRequestedForMainFrame` property.
[get_Kind](#get_kind) | Gets the `Kind` property.
[get_LinkText](#get_linktext) | Gets the `LinkText` property.
[get_LinkUri](#get_linkuri) | Gets the `LinkUri` property.
[get_PageUri](#get_pageuri) | Gets the `PageUri` property.
[get_SelectionText](#get_selectiontext) | Gets the `SelectionText` property.
[get_SourceUri](#get_sourceuri) | Gets the `SourceUri` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_FrameUri

Gets the `FrameUri` property.

> public HRESULT [get_FrameUri](#get_frameuri)(LPWSTR * value)

#### get_HasLinkText

Gets the `HasLinkText` property.

> public HRESULT [get_HasLinkText](#get_haslinktext)(BOOL * value)

#### get_HasLinkUri

Gets the `HasLinkUri` property.

> public HRESULT [get_HasLinkUri](#get_haslinkuri)(BOOL * value)

#### get_HasSelection

Gets the `HasSelection` property.

> public HRESULT [get_HasSelection](#get_hasselection)(BOOL * value)

#### get_HasSourceUri

Gets the `HasSourceUri` property.

> public HRESULT [get_HasSourceUri](#get_hassourceuri)(BOOL * value)

#### get_IsEditable

Gets the `IsEditable` property.

> public HRESULT [get_IsEditable](#get_iseditable)(BOOL * value)

#### get_IsRequestedForMainFrame

Gets the `IsRequestedForMainFrame` property.

> public HRESULT [get_IsRequestedForMainFrame](#get_isrequestedformainframe)(BOOL * value)

#### get_Kind

Gets the `Kind` property.

> public HRESULT [get_Kind](#get_kind)(COREWEBVIEW2_CONTEXT_MENU_TARGET_KIND * value)

#### get_LinkText

Gets the `LinkText` property.

> public HRESULT [get_LinkText](#get_linktext)(LPWSTR * value)

#### get_LinkUri

Gets the `LinkUri` property.

> public HRESULT [get_LinkUri](#get_linkuri)(LPWSTR * value)

#### get_PageUri

Gets the `PageUri` property.

> public HRESULT [get_PageUri](#get_pageuri)(LPWSTR * value)

#### get_SelectionText

Gets the `SelectionText` property.

> public HRESULT [get_SelectionText](#get_selectiontext)(LPWSTR * value)

#### get_SourceUri

Gets the `SourceUri` property.

> public HRESULT [get_SourceUri](#get_sourceuri)(LPWSTR * value)

