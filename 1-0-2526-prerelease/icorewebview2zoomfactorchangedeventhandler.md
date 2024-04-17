---
description: Implements the interface to receive `ZoomFactorChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ZoomFactorChangedEventHandler
ms.date: 04/22/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ZoomFactorChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2ZoomFactorChangedEventHandler
- ICoreWebView2ZoomFactorChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
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

> public HRESULT [Invoke](#invoke)([ICoreWebView2Controller](icorewebview2controller.md#icorewebview2controller) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

