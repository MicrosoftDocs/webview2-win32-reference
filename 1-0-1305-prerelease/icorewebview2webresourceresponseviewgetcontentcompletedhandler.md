---
description: Receives the result of the ICoreWebView2WebResourceResponseView::GetContent method.
title: WebView2 Win32 C++ ICoreWebView2WebResourceResponseViewGetContentCompletedHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebResourceResponseViewGetContentCompletedHandler
---

# interface ICoreWebView2WebResourceResponseViewGetContentCompletedHandler

```
interface ICoreWebView2WebResourceResponseViewGetContentCompletedHandler
  : public IUnknown
```

Receives the result of the [ICoreWebView2WebResourceResponseView::GetContent](icorewebview2webresourceresponseview.md) method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the completion status and result of the corresponding asynchronous method call.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### Invoke

Provides the completion status and result of the corresponding asynchronous method call.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, IStream * content)

A failure `errorCode` will be passed if the content failed to load. `E_ABORT` means the response loading was blocked (e.g., by CORS policy); `ERROR_CANCELLED` means the response loading was cancelled. `ERROR_NO_DATA` means the response has no content data, `content` is `null` in this case. Note content (if any) is ignored for redirects, 204 No Content, 205 Reset Content, and HEAD-request responses.

