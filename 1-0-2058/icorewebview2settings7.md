---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings7
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings7
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings7
- ICoreWebView2Settings7.get_HiddenPdfToolbarItems
- ICoreWebView2Settings7.put_HiddenPdfToolbarItems
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings7

```
interface ICoreWebView2Settings7
  : public ICoreWebView2Settings6
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HiddenPdfToolbarItems](#get_hiddenpdftoolbaritems) | Gets the `HiddenPdfToolbarItems` property.
[put_HiddenPdfToolbarItems](#put_hiddenpdftoolbaritems) | Sets the `HiddenPdfToolbarItems` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_HiddenPdfToolbarItems

Gets the `HiddenPdfToolbarItems` property.

> public HRESULT [get_HiddenPdfToolbarItems](#get_hiddenpdftoolbaritems)(COREWEBVIEW2_PDF_TOOLBAR_ITEMS * value)

#### put_HiddenPdfToolbarItems

Sets the `HiddenPdfToolbarItems` property.

> public HRESULT [put_HiddenPdfToolbarItems](#put_hiddenpdftoolbaritems)(COREWEBVIEW2_PDF_TOOLBAR_ITEMS value)

