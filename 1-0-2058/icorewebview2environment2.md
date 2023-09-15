---
description: 
title: WebView2 Win32 C++ ICoreWebView2Environment2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Environment2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Environment2
- ICoreWebView2Environment2.CreateWebResourceRequest
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Environment2

```
interface ICoreWebView2Environment2
  : public ICoreWebView2Environment
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateWebResourceRequest](#createwebresourcerequest) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### CreateWebResourceRequest

> public HRESULT [CreateWebResourceRequest](#createwebresourcerequest)(LPCWSTR uri, LPCWSTR Method, IStream * postData, LPCWSTR Headers, [ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) ** value)

