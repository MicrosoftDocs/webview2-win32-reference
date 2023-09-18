---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebMessageReceivedEventArgs
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebMessageReceivedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebMessageReceivedEventArgs
- ICoreWebView2WebMessageReceivedEventArgs.get_Source
- ICoreWebView2WebMessageReceivedEventArgs.get_WebMessageAsJson
- ICoreWebView2WebMessageReceivedEventArgs.TryGetWebMessageAsString
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebMessageReceivedEventArgs

```
interface ICoreWebView2WebMessageReceivedEventArgs
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Source](#get_source) | Gets the `Source` property.
[get_WebMessageAsJson](#get_webmessageasjson) | Gets the `WebMessageAsJson` property.
[TryGetWebMessageAsString](#trygetwebmessageasstring) | 

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### get_Source

Gets the `Source` property.

> public HRESULT [get_Source](#get_source)(LPWSTR * value)

#### get_WebMessageAsJson

Gets the `WebMessageAsJson` property.

> public HRESULT [get_WebMessageAsJson](#get_webmessageasjson)(LPWSTR * value)

#### TryGetWebMessageAsString

> public HRESULT [TryGetWebMessageAsString](#trygetwebmessageasstring)(LPWSTR * value)

