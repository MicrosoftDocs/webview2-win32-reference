---
description: 
title: WebView2 Win32 C++ ICoreWebView2Profile3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Profile3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Profile3
- ICoreWebView2Profile3.get_PreferredTrackingPreventionLevel
- ICoreWebView2Profile3.put_PreferredTrackingPreventionLevel
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Profile3

```
interface ICoreWebView2Profile3
  : public ICoreWebView2Profile2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_PreferredTrackingPreventionLevel](#get_preferredtrackingpreventionlevel) | Gets the `PreferredTrackingPreventionLevel` property.
[put_PreferredTrackingPreventionLevel](#put_preferredtrackingpreventionlevel) | Sets the `PreferredTrackingPreventionLevel` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1619

## Members

#### get_PreferredTrackingPreventionLevel

Gets the `PreferredTrackingPreventionLevel` property.

> public HRESULT [get_PreferredTrackingPreventionLevel](#get_preferredtrackingpreventionlevel)(COREWEBVIEW2_TRACKING_PREVENTION_LEVEL * value)

#### put_PreferredTrackingPreventionLevel

Sets the `PreferredTrackingPreventionLevel` property.

> public HRESULT [put_PreferredTrackingPreventionLevel](#put_preferredtrackingpreventionlevel)(COREWEBVIEW2_TRACKING_PREVENTION_LEVEL value)

