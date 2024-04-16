---
description: This interface is used to complete deferrals on event args that support getting deferrals using the `GetDeferral` method.
title: WebView2 Win32 C++ ICoreWebView2Deferral
ms.date: 04/16/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Deferral
topic_type: 
- APIRef
api_name:
- ICoreWebView2Deferral
- ICoreWebView2Deferral.Complete
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Deferral

```
interface ICoreWebView2Deferral
  : public IUnknown
```

This interface is used to complete deferrals on event args that support getting deferrals using the `GetDeferral` method.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[Complete](#complete) | Completes the associated deferred event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### Complete

Completes the associated deferred event.

> public HRESULT [Complete](#complete)()

Complete should only be run once for each deferral taken.

