---
description: Event args for the MoveFocusRequested event.
title: WebView2 Win32 C++ ICoreWebView2MoveFocusRequestedEventArgs
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 11/20/2020
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2MoveFocusRequestedEventArgs
---

# interface ICoreWebView2MoveFocusRequestedEventArgs 

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2MoveFocusRequestedEventArgs
  : public IUnknown
```

Event args for the MoveFocusRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Indicate whether the event has been handled by the app.
[get_Reason](#get_reason) | The reason for WebView to fire the MoveFocus Requested event.
[put_Handled](#put_handled) | Set the Handled property.

## Members

#### get_Handled 

Indicate whether the event has been handled by the app.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

If the app has moved the focus to its desired location, it should set Handled property to TRUE. When Handled property is false after the event handler returns, default action will be taken. The default action is to try to find the next tab stop child window in the app and try to move focus to that window. If there is no other such window to move focus to, focus will be cycled within the WebView's web content.

#### get_Reason 

The reason for WebView to fire the MoveFocus Requested event.

> public HRESULT [get_Reason](#get_reason)(COREWEBVIEW2_MOVE_FOCUS_REASON * reason)

#### put_Handled 

Set the Handled property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

