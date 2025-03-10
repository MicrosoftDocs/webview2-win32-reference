---
description: Event args for the `WebResourceRequested` event.
title: WebView2 Win32 C++ ICoreWebView2WebResourceRequestedEventArgs2
ms.date: 03/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceRequestedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebResourceRequestedEventArgs2
- ICoreWebView2WebResourceRequestedEventArgs2.get_RequestedSourceKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebResourceRequestedEventArgs2

```
interface ICoreWebView2WebResourceRequestedEventArgs2
  : public ICoreWebView2WebResourceRequestedEventArgs
```

Event args for the `WebResourceRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_RequestedSourceKind](#get_requestedsourcekind) | The web resource requested source.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2365.46
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### get_RequestedSourceKind

The web resource requested source.

> public HRESULT [get_RequestedSourceKind](#get_requestedsourcekind)(COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS * value)

