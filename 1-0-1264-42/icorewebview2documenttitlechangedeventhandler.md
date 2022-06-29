---
description: Receives `DocumentTitleChanged` events.
title: WebView2 Win32 C++ ICoreWebView2DocumentTitleChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DocumentTitleChangedEventHandler
---

# interface ICoreWebView2DocumentTitleChangedEventHandler

```
interface ICoreWebView2DocumentTitleChangedEventHandler
  : public IUnknown
```

Receives `DocumentTitleChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the `DocumentTitle` property to get the modified title.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

