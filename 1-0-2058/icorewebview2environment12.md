---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment12
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment12
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment12
- ICoreWebView2Environment12.CreateSharedBuffer
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment12

```
interface ICoreWebView2Environment12
  : public ICoreWebView2Environment11
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateSharedBuffer](#createsharedbuffer) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### CreateSharedBuffer

> public HRESULT [CreateSharedBuffer](#createsharedbuffer)(UINT64 Size, [ICoreWebView2SharedBuffer](icorewebview2sharedbuffer.md) ** value)

