---
description: Implements the interface to receive `IsMutedChanged` events.
title: WebView2 Win32 C++ ICoreWebView2IsMutedChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2IsMutedChangedEventHandler
---

# interface ICoreWebView2IsMutedChangedEventHandler

```
interface ICoreWebView2IsMutedChangedEventHandler
  : public IUnknown
```

Implements the interface to receive `IsMutedChanged` events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

Use the IsMuted property to get the mute state.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1072.54
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2 * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

