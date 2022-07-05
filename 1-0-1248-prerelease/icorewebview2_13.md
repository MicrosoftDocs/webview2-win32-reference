---
description: This interface is an extension of ICoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2_13
ms.date: 07/05/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_13
---

# interface ICoreWebView2_13

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_13
  : public ICoreWebView2_12
```

This interface is an extension of ICoreWebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Profile](#get_profile) | The associated ICoreWebView2Profile object.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### get_Profile

The associated ICoreWebView2Profile object.

> public HRESULT [get_Profile](#get_profile)(ICoreWebView2Profile ** value)

If this CoreWebView2 was created with a CoreWebView2ControllerOptions, the CoreWebView2Profile will match those specified options. Otherwise if this CoreWebView2 was created without a CoreWebView2ControllerOptions, then this will be the default CoreWebView2Profile for the corresponding CoreWebView2Environment.

