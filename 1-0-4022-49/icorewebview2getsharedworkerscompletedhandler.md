---
description: Receives the result of the `GetSharedWorkers` method.
title: WebView2 Win32 C++ ICoreWebView2GetSharedWorkersCompletedHandler
ms.date: 06/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetSharedWorkersCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2GetSharedWorkersCompletedHandler
- ICoreWebView2GetSharedWorkersCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2GetSharedWorkersCompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2GetSharedWorkersCompletedHandler
  : public IUnknown
```

Receives the result of the `GetSharedWorkers` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.4015

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2SharedWorkerCollectionView](icorewebview2sharedworkercollectionview.md#icorewebview2sharedworkercollectionview) * result)

