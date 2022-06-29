---
description: Implements the interface to receive `ZoomFactorChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ZoomFactorChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ZoomFactorChangedEventHandler
---

# interface ICoreWebView2ZoomFactorChangedEventHandler

```
interface ICoreWebView2ZoomFactorChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `ZoomFactorChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the `ICoreWebView2Controller.ZoomFactor` property to get the modified zoom factor.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2Controller * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

