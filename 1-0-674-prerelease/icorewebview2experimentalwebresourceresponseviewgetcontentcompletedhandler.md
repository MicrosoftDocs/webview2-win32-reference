---
description: The caller implements this interface to receive the result of the ICoreWebView2WebResourceResponseView::GetContent method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalWebResourceResponseViewGetContentCompletedHandler
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/23/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalWebResourceResponseViewGetContentCompletedHandler
---

# interface ICoreWebView2ExperimentalWebResourceResponseViewGetContentCompletedHandler 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalWebResourceResponseViewGetContentCompletedHandler
  : public IUnknown
```

The caller implements this interface to receive the result of the ICoreWebView2WebResourceResponseView::GetContent method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

## Members

#### Invoke 

Called to provide the implementer with the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, IStream * content)

A failure errorCode will be passed if the content failed to load. Null means no content was found. Note content (if any) for redirect responses is ignored.

