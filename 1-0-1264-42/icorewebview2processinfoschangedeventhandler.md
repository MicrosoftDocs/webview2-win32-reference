---
description: An event handler for the `ProcessInfosChanged` event.
title: WebView2 Win32 C++ ICoreWebView2ProcessInfosChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ProcessInfosChangedEventHandler
---

# interface ICoreWebView2ProcessInfosChangedEventHandler

```
interface ICoreWebView2ProcessInfosChangedEventHandler
  : public IUnknown
```

An event handler for the `ProcessInfosChanged` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2Environment * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

