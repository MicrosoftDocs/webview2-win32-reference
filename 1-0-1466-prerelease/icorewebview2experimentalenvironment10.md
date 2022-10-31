---
description: This is the ICoreWebView2Environment Experimental interface for creating shared buffer object.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironment10
ms.date: 10/31/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironment10
---

# interface ICoreWebView2ExperimentalEnvironment10

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironment10
  : public IUnknown
```

This is the [ICoreWebView2Environment](icorewebview2environment.md) Experimental interface for creating shared buffer object.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateSharedBuffer](#createsharedbuffer) | Create a shared memory based buffer with the specified size in bytes.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### CreateSharedBuffer

Create a shared memory based buffer with the specified size in bytes.

> public HRESULT [CreateSharedBuffer](#createsharedbuffer)(UINT64 size, [ICoreWebView2ExperimentalSharedBuffer](icorewebview2experimentalsharedbuffer.md) ** shared_buffer)

The buffer can be shared with web contents in WebView by calling `PostSharedBufferToScript` on `CoreWebView2` or `CoreWebView2Frame` object. Once shared, the same content of the buffer will be accessible from both the app process and script in WebView. Modification to the content will be visible to all parties that have access to the buffer. The shared buffer is presented to the script as ArrayBuffer. All JavaScript APIs that work for ArrayBuffer including Atomics APIs can be used on it.

