---
description: An event handler for the `ProcessInfosChanged` event.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProcessInfosChangedEventHandler
ms.date: 11/29/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProcessInfosChangedEventHandler
---

# interface ICoreWebView2ExperimentalProcessInfosChangedEventHandler

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProcessInfosChangedEventHandler
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
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1083

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)(ICoreWebView2Environment * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

