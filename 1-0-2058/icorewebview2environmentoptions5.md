---
description: 
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions5
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions5
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions5
- ICoreWebView2EnvironmentOptions5.get_EnableTrackingPrevention
- ICoreWebView2EnvironmentOptions5.put_EnableTrackingPrevention
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions5

```
interface ICoreWebView2EnvironmentOptions5
  : public ICoreWebView2EnvironmentOptions4
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_EnableTrackingPrevention](#get_enabletrackingprevention) | Gets the `EnableTrackingPrevention` property.
[put_EnableTrackingPrevention](#put_enabletrackingprevention) | Sets the `EnableTrackingPrevention` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1661.34
WebView2 Win32 Prerelease |    1.0.1619

## Members

#### get_EnableTrackingPrevention

Gets the `EnableTrackingPrevention` property.

> public HRESULT [get_EnableTrackingPrevention](#get_enabletrackingprevention)(BOOL * value)

#### put_EnableTrackingPrevention

Sets the `EnableTrackingPrevention` property.

> public HRESULT [put_EnableTrackingPrevention](#put_enabletrackingprevention)(BOOL value)

