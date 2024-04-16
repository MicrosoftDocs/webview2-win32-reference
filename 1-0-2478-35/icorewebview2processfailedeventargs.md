---
description: Event args for the `ProcessFailed` event.
title: WebView2 Win32 C++ ICoreWebView2ProcessFailedEventArgs
ms.date: 04/16/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessFailedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProcessFailedEventArgs
- ICoreWebView2ProcessFailedEventArgs.get_ProcessFailedKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProcessFailedEventArgs

```
interface ICoreWebView2ProcessFailedEventArgs
  : public IUnknown
```

Event args for the `ProcessFailed` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ProcessFailedKind](#get_processfailedkind) | The kind of process failure that has occurred.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_ProcessFailedKind

The kind of process failure that has occurred.

> public HRESULT [get_ProcessFailedKind](#get_processfailedkind)(COREWEBVIEW2_PROCESS_FAILED_KIND * processFailedKind)

This is a combination of process kind (for example, browser, renderer, gpu) and failure (exit, unresponsiveness). Renderer processes are further divided in *main frame* renderer (`RenderProcessExited`, `RenderProcessUnresponsive`) and *subframe* renderer (`FrameRenderProcessExited`). To learn about the conditions under which each failure kind occurs, see `COREWEBVIEW2_PROCESS_FAILED_KIND`.

