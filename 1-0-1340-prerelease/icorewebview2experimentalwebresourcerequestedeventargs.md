---
description: Event args for the `WebResourceRequested` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalWebResourceRequestedEventArgs
ms.date: 08/04/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalWebResourceRequestedEventArgs
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
WebView2 Win32 Prerelease |    

## Members

#### get_RequestedSourceKind

The web resource requested source.

> public HRESULT [get_RequestedSourceKind](#get_requestedsourcekind)(COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS * requestedSourceKind)

