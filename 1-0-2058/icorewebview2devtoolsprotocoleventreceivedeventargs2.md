---
description: 
title: WebView2 Win32 C++ ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
- ICoreWebView2DevToolsProtocolEventReceivedEventArgs2.get_SessionId
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2DevToolsProtocolEventReceivedEventArgs2

```
interface ICoreWebView2DevToolsProtocolEventReceivedEventArgs2
  : public ICoreWebView2DevToolsProtocolEventReceivedEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_SessionId](#get_sessionid) | Gets the `SessionId` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1185.39
WebView2 Win32 Prerelease |    1.0.1189

## Members

#### get_SessionId

Gets the `SessionId` property.

> public HRESULT [get_SessionId](#get_sessionid)(LPWSTR * value)

