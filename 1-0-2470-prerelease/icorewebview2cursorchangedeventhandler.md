---
description: The caller implements this interface to receive CursorChanged events.
title: WebView2 Win32 C++ ICoreWebView2CursorChangedEventHandler
ms.date: 03/25/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CursorChangedEventHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2CursorChangedEventHandler
- ICoreWebView2CursorChangedEventHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CursorChangedEventHandler

```
interface ICoreWebView2CursorChangedEventHandler
  : public IUnknown
```

The caller implements this interface to receive CursorChanged events.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Called to provide the implementer with the event args for the corresponding event.

Use the Cursor property to get the new cursor.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.790

## Members

#### Invoke

Called to provide the implementer with the event args for the corresponding event.

> public HRESULT [Invoke](#invoke)([ICoreWebView2CompositionController](icorewebview2compositioncontroller.md#icorewebview2compositioncontroller) * sender, IUnknown * args)

There are no event args and the args parameter will be null.

