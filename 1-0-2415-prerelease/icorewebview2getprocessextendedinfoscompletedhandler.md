---
description: Receives the result of the `GetProcessExtendedInfos` method.
title: WebView2 Win32 C++ ICoreWebView2GetProcessExtendedInfosCompletedHandler
ms.date: 02/26/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2GetProcessExtendedInfosCompletedHandler
topic_type: 
- APIRef
api_name:
- ICoreWebView2GetProcessExtendedInfosCompletedHandler
- ICoreWebView2GetProcessExtendedInfosCompletedHandler.Invoke
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2GetProcessExtendedInfosCompletedHandler

```
interface ICoreWebView2GetProcessExtendedInfosCompletedHandler
  : public IUnknown
```

Receives the result of the `GetProcessExtendedInfos` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the process extended info list for the `GetProcessExtendedInfos`.

The result is written to the collection of `ProcessExtendedInfo`s provided in the `GetProcessExtendedInfos` method call.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### Invoke

Provides the process extended info list for the `GetProcessExtendedInfos`.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, ICoreWebView2ProcessExtendedInfoCollection * value)

