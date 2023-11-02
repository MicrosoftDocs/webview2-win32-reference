---
description: Event args for the `WebResourceRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalWebResourceRequestedEventArgs
ms.date: 11/06/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalWebResourceRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalWebResourceRequestedEventArgs
- ICoreWebView2ExperimentalWebResourceRequestedEventArgs.get_RequestedSourceKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalWebResourceRequestedEventArgs

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalWebResourceRequestedEventArgs
  : public IUnknown
```

Event args for the `WebResourceRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_RequestedSourceKind](#get_requestedsourcekind) | The web resource requested source.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1340

## Members

#### get_RequestedSourceKind

The web resource requested source.

> public HRESULT [get_RequestedSourceKind](#get_requestedsourcekind)(COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS * requestedSourceKind)

