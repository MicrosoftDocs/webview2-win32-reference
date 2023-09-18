---
description: 
title: WebView2 Win32 C++ ICoreWebView2Frame4
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame4
topic_type: 
- APIRef
api_name:
- ICoreWebView2Frame4
- ICoreWebView2Frame4.PostSharedBufferToScript
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Frame4

```
interface ICoreWebView2Frame4
  : public ICoreWebView2Frame3
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[PostSharedBufferToScript](#postsharedbuffertoscript) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1671

## Members

#### PostSharedBufferToScript

> public HRESULT [PostSharedBufferToScript](#postsharedbuffertoscript)([ICoreWebView2SharedBuffer](icorewebview2sharedbuffer.md) * sharedBuffer, COREWEBVIEW2_SHARED_BUFFER_ACCESS access, LPCWSTR additionalDataAsJson)

