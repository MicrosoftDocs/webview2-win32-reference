---
description: 
title: WebView2 Win32 C++ ICoreWebView2WebMessageReceivedEventArgs2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2WebMessageReceivedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2WebMessageReceivedEventArgs2
- ICoreWebView2WebMessageReceivedEventArgs2.get_AdditionalObjects
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2WebMessageReceivedEventArgs2

```
interface ICoreWebView2WebMessageReceivedEventArgs2
  : public ICoreWebView2WebMessageReceivedEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalObjects](#get_additionalobjects) | Gets the `AdditionalObjects` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1774.30
WebView2 Win32 Prerelease |    1.0.1777

## Members

#### get_AdditionalObjects

Gets the `AdditionalObjects` property.

> public HRESULT [get_AdditionalObjects](#get_additionalobjects)(VARIANTCollection ** value)

