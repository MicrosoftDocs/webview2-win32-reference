---
description: 
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventArgs2
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventArgs2
topic_type: 
- APIRef
api_name:
- ICoreWebView2NavigationStartingEventArgs2
- ICoreWebView2NavigationStartingEventArgs2.get_AdditionalAllowedFrameAncestors
- ICoreWebView2NavigationStartingEventArgs2.put_AdditionalAllowedFrameAncestors
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NavigationStartingEventArgs2

```
interface ICoreWebView2NavigationStartingEventArgs2
  : public ICoreWebView2NavigationStartingEventArgs
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalAllowedFrameAncestors](#get_additionalallowedframeancestors) | Gets the `AdditionalAllowedFrameAncestors` property.
[put_AdditionalAllowedFrameAncestors](#put_additionalallowedframeancestors) | Sets the `AdditionalAllowedFrameAncestors` property.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_AdditionalAllowedFrameAncestors

Gets the `AdditionalAllowedFrameAncestors` property.

> public HRESULT [get_AdditionalAllowedFrameAncestors](#get_additionalallowedframeancestors)(LPWSTR * value)

#### put_AdditionalAllowedFrameAncestors

Sets the `AdditionalAllowedFrameAncestors` property.

> public HRESULT [put_AdditionalAllowedFrameAncestors](#put_additionalallowedframeancestors)(LPCWSTR value)

