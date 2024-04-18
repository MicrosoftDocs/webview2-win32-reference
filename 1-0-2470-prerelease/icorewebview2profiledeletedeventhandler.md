---
description: Receives the `CoreWebView2Profile.Deleted` event.
title: WebView2 Win32 C++ ICoreWebView2ProfileDeletedEventHandler
ms.date: 04/22/2024
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2ProfileDeletedEventHandler
  : public IUnknown
```

Receives the `CoreWebView2Profile.Deleted` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the profile deleted event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2194

## Members

#### Invoke

Called to provide the implementer with the event args for the profile deleted event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

