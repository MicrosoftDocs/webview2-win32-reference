---
description: Receives `Deleted` events.
title: WebView2 Win32 C++ ICoreWebView2ProfileDeletedEventHandler
ms.date: 07/08/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProfileDeletedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ProfileDeletedEventHandler
- ICoreWebView2ProfileDeletedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ProfileDeletedEventHandler

```
interface ICoreWebView2ProfileDeletedEventHandler
  : public IUnknown
```

Receives `Deleted` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) * sender, IUnknown * args)

