---
description: 
title: WebView2 Win32 C++ ICoreWebView2PermissionRequestedEventArgs2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2PermissionRequestedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2PermissionRequestedEventArgs2
- ICoreWebView2PermissionRequestedEventArgs2.get_Handled
- ICoreWebView2PermissionRequestedEventArgs2.put_Handled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2PermissionRequestedEventArgs2

```
interface ICoreWebView2PermissionRequestedEventArgs2
  : public ICoreWebView2PermissionRequestedEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Handled](#get_handled) | Gets the `Handled` property.
[put_Handled](#put_handled) | Sets the `Handled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1158

## Members

#### get_Handled

Gets the `Handled` property.

> public HRESULT [get_Handled](#get_handled)(BOOL * value)

#### put_Handled

Sets the `Handled` property.

> public HRESULT [put_Handled](#put_handled)(BOOL value)

