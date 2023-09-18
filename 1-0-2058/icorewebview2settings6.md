---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings6
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings6
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings6
- ICoreWebView2Settings6.get_IsSwipeNavigationEnabled
- ICoreWebView2Settings6.put_IsSwipeNavigationEnabled
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings6

```
interface ICoreWebView2Settings6
  : public ICoreWebView2Settings5
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsSwipeNavigationEnabled](#get_isswipenavigationenabled) | Gets the `IsSwipeNavigationEnabled` property.
[put_IsSwipeNavigationEnabled](#put_isswipenavigationenabled) | Sets the `IsSwipeNavigationEnabled` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.992.28
WebView2 Win32 Prerelease |    1.0.1010

## Members

#### get_IsSwipeNavigationEnabled

Gets the `IsSwipeNavigationEnabled` property.

> public HRESULT [get_IsSwipeNavigationEnabled](#get_isswipenavigationenabled)(BOOL * value)

#### put_IsSwipeNavigationEnabled

Sets the `IsSwipeNavigationEnabled` property.

> public HRESULT [put_IsSwipeNavigationEnabled](#put_isswipenavigationenabled)(BOOL value)

