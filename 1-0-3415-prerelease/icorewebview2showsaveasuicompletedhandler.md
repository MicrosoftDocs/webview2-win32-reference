---
description: Receives the result of the `ShowSaveAsUI` method.
title: WebView2 Win32 C++ ICoreWebView2ShowSaveAsUICompletedHandler
ms.date: 07/08/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ShowSaveAsUICompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ShowSaveAsUICompletedHandler
- ICoreWebView2ShowSaveAsUICompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ShowSaveAsUICompletedHandler

```
interface ICoreWebView2ShowSaveAsUICompletedHandler
  : public IUnknown
```

Receives the result of the `ShowSaveAsUI` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2739.15
WebView2 Win32 Prerelease |    1.0.2730

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, COREWEBVIEW2_SAVE_AS_UI_RESULT result)

