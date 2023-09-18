---
description: 
title: WebView2 Win32 C++ ICoreWebView2SourceChangedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SourceChangedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2SourceChangedEventArgs
- ICoreWebView2SourceChangedEventArgs.get_IsNewDocument
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SourceChangedEventArgs

```
interface ICoreWebView2SourceChangedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsNewDocument](#get_isnewdocument) | Gets the `IsNewDocument` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_IsNewDocument

Gets the `IsNewDocument` property.

> public HRESULT [get_IsNewDocument](#get_isnewdocument)(BOOL * value)

