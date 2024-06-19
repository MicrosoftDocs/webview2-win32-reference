---
description: Receives the result of the `ShowSaveAsUI` method.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalShowSaveAsUICompletedHandler
ms.date: 06/19/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalShowSaveAsUICompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalShowSaveAsUICompletedHandler
- ICoreWebView2ExperimentalShowSaveAsUICompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalShowSaveAsUICompletedHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalShowSaveAsUICompletedHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2526

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, COREWEBVIEW2_SAVE_AS_UI_RESULT result)

