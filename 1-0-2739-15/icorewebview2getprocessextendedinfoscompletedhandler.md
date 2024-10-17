---
description: Receives the result of the `GetProcessExtendedInfos` method.
title: WebView2 Win32 C++ ICoreWebView2GetProcessExtendedInfosCompletedHandler
ms.date: 08/26/2024
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

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2GetProcessExtendedInfosCompletedHandler
  : public IUnknown
```

Receives the result of the `GetProcessExtendedInfos` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Invoke](#invoke) | Provides the result of the corresponding asynchronous method.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.2210.55
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### Invoke

Provides the result of the corresponding asynchronous method.

> public HRESULT [Invoke](#invoke)(HRESULT errorCode, [ICoreWebView2ProcessExtendedInfoCollection](icorewebview2processextendedinfocollection.md#icorewebview2processextendedinfocollection) * result)

