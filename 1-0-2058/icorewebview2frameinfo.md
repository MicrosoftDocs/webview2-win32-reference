---
description: 
title: WebView2 Win32 C++ ICoreWebView2FrameInfo
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2FrameInfo
topic_type: 
- APIRef
api_name:
- ICoreWebView2FrameInfo
- ICoreWebView2FrameInfo.get_Name
- ICoreWebView2FrameInfo.get_Source
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2FrameInfo

```
interface ICoreWebView2FrameInfo
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Name](#get_name) | Gets the `Name` property.
[get_Source](#get_source) | Gets the `Source` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.818.41
WebView2 Win32 Prerelease |    1.0.824

## Members

#### get_Name

Gets the `Name` property.

> public HRESULT [get_Name](#get_name)(LPWSTR * value)

#### get_Source

Gets the `Source` property.

> public HRESULT [get_Source](#get_source)(LPWSTR * value)

