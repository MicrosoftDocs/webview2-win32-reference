---
description: Receives `IsDefaultDownloadDialogOpenChanged` events.
title: WebView2 Win32 C++ ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler
ms.date: 07/08/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler
- ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2IsDefaultDownloadDialogOpenChangedEventHandler
  : public IUnknown
```

Receives `IsDefaultDownloadDialogOpenChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md#icorewebview2) * sender, IUnknown * args)

