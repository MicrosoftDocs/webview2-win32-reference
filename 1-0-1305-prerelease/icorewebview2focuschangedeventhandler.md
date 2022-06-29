---
description: Receives `GotFocus` and `LostFocus` events.
title: WebView2 Win32 C++ ICoreWebView2FocusChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FocusChangedEventHandler
---

# interface ICoreWebView2FocusChangedEventHandler

```
interface ICoreWebView2FocusChangedEventHandler
  : public IUnknown
```

Receives `GotFocus` and `LostFocus` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Controller](icorewebview2controller.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

