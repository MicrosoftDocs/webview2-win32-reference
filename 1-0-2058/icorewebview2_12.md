---
description: 
title: WebView2 Win32 C++ ICoreWebView2_12
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_12
topic_type: 
- APIRef
api_name:
- ICoreWebView2_12
- ICoreWebView2_12.add_StatusBarTextChanged
- ICoreWebView2_12.get_StatusBarText
- ICoreWebView2_12.remove_StatusBarTextChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_12

```
interface ICoreWebView2_12
  : public ICoreWebView2_11
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_StatusBarTextChanged](#add_statusbartextchanged) | Adds an event handler for the `StatusBarTextChanged` event.
[get_StatusBarText](#get_statusbartext) | Gets the `StatusBarText` property.
[remove_StatusBarTextChanged](#remove_statusbartextchanged) | Removes an event handler previously added with `add_StatusBarTextChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### add_StatusBarTextChanged

Adds an event handler for the `StatusBarTextChanged` event.

> public HRESULT [add_StatusBarTextChanged](#add_statusbartextchanged)([ICoreWebView2StatusBarTextChangedEventHandler](icorewebview2statusbartextchangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_StatusBarText

Gets the `StatusBarText` property.

> public HRESULT [get_StatusBarText](#get_statusbartext)(LPWSTR * value)

#### remove_StatusBarTextChanged

Removes an event handler previously added with `add_StatusBarTextChanged`.

> public HRESULT [remove_StatusBarTextChanged](#remove_statusbartextchanged)(EventRegistrationToken token)

