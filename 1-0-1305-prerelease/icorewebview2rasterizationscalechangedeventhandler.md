---
description: Receives `RasterizationScaleChanged` events.
title: WebView2 Win32 C++ ICoreWebView2RasterizationScaleChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2RasterizationScaleChangedEventHandler
---

# interface ICoreWebView2RasterizationScaleChangedEventHandler

```
interface ICoreWebView2RasterizationScaleChangedEventHandler
  : public IUnknown
```

Receives `RasterizationScaleChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

Use the `RasterizationScale` property to get the modified scale.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### Invoke

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2Controller](icorewebview2controller.md) * sender, IUnknown * args)

There are no event args and the args parameter will be null.

