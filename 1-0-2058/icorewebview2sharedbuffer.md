---
description: 
title: WebView2 Win32 C++ ICoreWebView2SharedBuffer
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SharedBuffer
topic_type: 
- APIRef
api_name:
- ICoreWebView2SharedBuffer
- ICoreWebView2SharedBuffer.get_Size
- ICoreWebView2SharedBuffer.OpenStream
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SharedBuffer

```
interface ICoreWebView2SharedBuffer
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Size](#get_size) | Gets the `Size` property.
[OpenStream](#openstream) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### get_Size

Gets the `Size` property.

> public HRESULT [get_Size](#get_size)(UINT64 * value)

#### OpenStream

> public HRESULT [OpenStream](#openstream)(IStream ** value)

