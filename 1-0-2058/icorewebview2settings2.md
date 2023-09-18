---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings2
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings2
- ICoreWebView2Settings2.get_UserAgent
- ICoreWebView2Settings2.put_UserAgent
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings2

```
interface ICoreWebView2Settings2
  : public ICoreWebView2Settings
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_UserAgent](#get_useragent) | Gets the `UserAgent` property.
[put_UserAgent](#put_useragent) | Sets the `UserAgent` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.864.35
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_UserAgent

Gets the `UserAgent` property.

> public HRESULT [get_UserAgent](#get_useragent)(LPWSTR * value)

#### put_UserAgent

Sets the `UserAgent` property.

> public HRESULT [put_UserAgent](#put_useragent)(LPCWSTR value)

