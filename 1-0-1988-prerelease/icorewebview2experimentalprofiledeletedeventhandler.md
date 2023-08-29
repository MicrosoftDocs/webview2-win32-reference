---
description: Receives the `CoreWebView2Profile.Deleted` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfileDeletedEventHandler
ms.date: 08/30/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfileDeletedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfileDeletedEventHandler
- ICoreWebView2ExperimentalProfileDeletedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfileDeletedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfileDeletedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### Invoke

Called to provide the implementer with the event args for the profile deleted event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Profile](icorewebview2profile.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

