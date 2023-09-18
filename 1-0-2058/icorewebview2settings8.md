---
description: 
title: WebView2 Win32 C++ ICoreWebView2Settings8
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Settings8
topic_type: 
- APIRef
api_name:
- ICoreWebView2Settings8
- ICoreWebView2Settings8.get_IsReputationCheckingRequired
- ICoreWebView2Settings8.put_IsReputationCheckingRequired
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Settings8

```
interface ICoreWebView2Settings8
  : public ICoreWebView2Settings7
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_IsReputationCheckingRequired](#get_isreputationcheckingrequired) | Gets the `IsReputationCheckingRequired` property.
[put_IsReputationCheckingRequired](#put_isreputationcheckingrequired) | Sets the `IsReputationCheckingRequired` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1722.45
WebView2 Win32 Prerelease |    1.0.1724

## Members

#### get_IsReputationCheckingRequired

Gets the `IsReputationCheckingRequired` property.

> public HRESULT [get_IsReputationCheckingRequired](#get_isreputationcheckingrequired)(BOOL * value)

#### put_IsReputationCheckingRequired

Sets the `IsReputationCheckingRequired` property.

> public HRESULT [put_IsReputationCheckingRequired](#put_isreputationcheckingrequired)(BOOL value)

