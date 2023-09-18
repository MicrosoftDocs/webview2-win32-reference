---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment3
- ICoreWebView2Environment3.CreateCoreWebView2CompositionController
- ICoreWebView2Environment3.CreateCoreWebView2PointerInfo
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment3

```
interface ICoreWebView2Environment3
  : public ICoreWebView2Environment2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateCoreWebView2CompositionController](#createcorewebview2compositioncontroller) | 
[CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### CreateCoreWebView2CompositionController

> public HRESULT [CreateCoreWebView2CompositionController](#createcorewebview2compositioncontroller)(HWND * ParentWindow, [ICoreWebView2CreateCoreWebView2CompositionControllerCompletedHandler](icorewebview2createcorewebview2compositioncontrollercompletedhandler.md) * handler)

#### CreateCoreWebView2PointerInfo

> public HRESULT [CreateCoreWebView2PointerInfo](#createcorewebview2pointerinfo)([ICoreWebView2PointerInfo](icorewebview2pointerinfo.md) ** value)

