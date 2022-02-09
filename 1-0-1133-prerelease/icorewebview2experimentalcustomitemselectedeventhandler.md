---
description: Raised to notify the host that the end user selected a custom `ContextMenuItem`.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalCustomItemSelectedEventHandler
ms.date: 02/09/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalCustomItemSelectedEventHandler
---

# interface ICoreWebView2ExperimentalCustomItemSelectedEventHandler

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalCustomItemSelectedEventHandler
  : public IUnknown
```

Raised to notify the host that the end user selected a custom `ContextMenuItem`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the event args for the corresponding event.

`CustomItemSelected` event is raised on the specific `ContextMenuItem` that the end user selected.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### Invoke

Provides the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2ExperimentalContextMenuItem](icorewebview2experimentalcontextmenuitem.md) * sender, IUnknown * args)

No event args exist and the `args` parameter is set to `null`.

