---
description: Receives the result of the `ICoreWebView2WebResourceResponseView::GetContent` method.
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponseViewGetContentCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
ms.prod: microsoft-edge
ms.technology: webview
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponseViewGetContentCompletedHandler
---

# interface ICoreWebView2WebResourceResponseViewGetContentCompletedHandler 

```
interface ICoreWebView2WebResourceResponseViewGetContentCompletedHandler
  : public IUnknown
```

Receives the result of the `[ICoreWebView2WebResourceResponseView::GetContent](icorewebview2webresourceresponseview.md)` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the completion status and result of the corresponding asynchronous method call.

## Members

#### Invoke 

Provides the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, IStream * content)

A failure `errorCode` will be passed if the content failed to load. `null` means no content was found. Note content (if any) for redirect responses is ignored.

