---
description: Interface that provides methods related to the environment settings of CoreWebView2.
title: WebView2 Win32 C++ ICoreWebView2Environment15
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment15
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment15
- ICoreWebView2Environment15.CreateFindOptions
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment15

```
interface ICoreWebView2Environment15
  : public ICoreWebView2Environment14
```

Interface that provides methods related to the environment settings of CoreWebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateFindOptions](#createfindoptions) | Creates a new instance of a CoreWebView2FindOptions object.

This interface allows for the creation of new `FindOptions` objects.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.3405.78
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### CreateFindOptions

Creates a new instance of a CoreWebView2FindOptions object.

> public HRESULT [CreateFindOptions](#createfindoptions)([ICoreWebView2FindOptions](icorewebview2findoptions.md#icorewebview2findoptions) ** value)

This find options object can be used to define parameters for a find session. Returns the newly created FindOptions object.

