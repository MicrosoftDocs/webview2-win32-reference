---
description: A continuation of the ICoreWebView2Environment interface for creating shared buffer object.
title: WebView2 Win32 C++ ICoreWebView2Environment12
ms.date: 12/11/2023
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2Environment12
  : public ICoreWebView2Environment11
```

A continuation of the [ICoreWebView2Environment](icorewebview2environment.md) interface for creating shared buffer object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateSharedBuffer](#createsharedbuffer) | Create a shared memory based buffer with the specified size in bytes.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### CreateSharedBuffer

Create a shared memory based buffer with the specified size in bytes.

> public HRESULT [CreateSharedBuffer](#createsharedbuffer)(UINT64 size, [ICoreWebView2SharedBuffer](icorewebview2sharedbuffer.md) ** shared_buffer)

The buffer can be shared with web contents in WebView by calling `PostSharedBufferToScript` on `CoreWebView2` or `CoreWebView2Frame` object. Once shared, the same content of the buffer will be accessible from both the app process and script in WebView. Modification to the content will be visible to all parties that have access to the buffer. The shared buffer is presented to the script as ArrayBuffer. All JavaScript APIs that work for ArrayBuffer including Atomics APIs can be used on it. There is currently a limitation that only size less than 2GB is supported.

