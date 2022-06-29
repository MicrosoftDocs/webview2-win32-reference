---
description: Event args for the `ProcessFailed` event.
title: WebView2 Win32 C++ ICoreWebView2ProcessFailedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessFailedEventArgs
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

`processFailedKind` is `COREWEBVIEW2_PROCESS_FAILED_KIND_RENDER_PROCESS_EXITED` if the failed process is the main frame's renderer, even if there were subframes rendered by such process; all frames are gone when this happens.

