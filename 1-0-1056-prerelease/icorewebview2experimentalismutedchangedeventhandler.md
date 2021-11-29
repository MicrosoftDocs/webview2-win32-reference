---
description: Implements the interface to receive `IsMutedChanged` events.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalIsMutedChangedEventHandler
ms.date: 11/29/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalIsMutedChangedEventHandler
---

# interface ICoreWebView2ExperimentalIsMutedChangedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalIsMutedChangedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1018

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

