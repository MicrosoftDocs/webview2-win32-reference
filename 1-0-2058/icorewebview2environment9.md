---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment9
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment9
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment9
- ICoreWebView2Environment9.CreateContextMenuItem
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment9

```
interface ICoreWebView2Environment9
  : public ICoreWebView2Environment8
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateContextMenuItem](#createcontextmenuitem) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### CreateContextMenuItem

> public HRESULT [CreateContextMenuItem](#createcontextmenuitem)(LPCWSTR Label, IStream * iconStream, COREWEBVIEW2_CONTEXT_MENU_ITEM_KIND Kind, [ICoreWebView2ContextMenuItem](icorewebview2contextmenuitem.md) ** value)

