---
description: Event args for the `MoveFocusRequested` event.
title: WebView2 Win32 C++ ICoreWebView2MoveFocusRequestedEventArgs
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2MoveFocusRequestedEventArgs
---

# interface ICoreWebView2MoveFocusRequestedEventArgs

```
interface ICoreWebView2MoveFocusRequestedEventArgs
  : public IUnknown
```

Event args for the `MoveFocusRequested` event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Indicates whether the event has been handled by the app.
[get_Reason](#get_reason) | The reason for WebView to run the `MoveFocusRequested` event.
[put_Handled](#put_handled) | Sets the `Handled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Handled

Indicates whether the event has been handled by the app.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

If the app has moved the focus to another desired location, it should set the `Handled` property to `TRUE`. When the `Handled` property is `FALSE` after the event handler returns, default action is taken. The default action is to try to find the next tab stop child window in the app and try to move focus to that window. If no other window exists to move focus, focus is cycled within the web content of the WebView.

#### get_Reason

The reason for WebView to run the `MoveFocusRequested` event.

> public HRESULT [get_Reason](#get_reason)(COREWEBVIEW2_MOVE_FOCUS_REASON * reason)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

