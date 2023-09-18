---
description: 
title: WebView2 Win32 C++ ICoreWebView2MoveFocusRequestedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2MoveFocusRequestedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2MoveFocusRequestedEventArgs
- ICoreWebView2MoveFocusRequestedEventArgs.get_Handled
- ICoreWebView2MoveFocusRequestedEventArgs.get_Reason
- ICoreWebView2MoveFocusRequestedEventArgs.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2MoveFocusRequestedEventArgs

```
interface ICoreWebView2MoveFocusRequestedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets the `Handled` property.
[get_Reason](#get_reason) | Gets the `Reason` property.
[put_Handled](#put_handled) | Sets the `Handled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### get_Reason

Gets the `Reason` property.

> public HRESULT [get_Reason](#get_reason)(COREWEBVIEW2_MOVE_FOCUS_REASON * value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

