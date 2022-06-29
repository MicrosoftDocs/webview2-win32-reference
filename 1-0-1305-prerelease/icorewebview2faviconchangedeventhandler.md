---
description: This interface is a handler for when the `Favicon` is changed.
title: WebView2 Win32 C++ ICoreWebView2FaviconChangedEventHandler
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FaviconChangedEventHandler
---

# interface ICoreWebView2FaviconChangedEventHandler

```
interface ICoreWebView2FaviconChangedEventHandler
  : public IUnknown
```

This interface is a handler for when the `Favicon` is changed.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to notify the favicon changed. The event args are always null.

The sender is the [ICoreWebView2](icorewebview2.md) object the top-level document of which has changed favicon and the eventArgs is nullptr. Use the FaviconUri property and GetFavicon method to obtain the favicon data. The second argument is always null. For more information see `add_FaviconChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### Invoke

Called to notify the favicon changed. The event args are always null.

> public HRESULT [Invoke](#invoke)([ICoreWebView2](icorewebview2.md) * sender, IUnknown * args)

