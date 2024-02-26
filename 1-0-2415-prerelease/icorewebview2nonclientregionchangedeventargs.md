---
description: This is the Interface for non-client region change event args.
title: WebView2 Win32 C++ ICoreWebView2NonClientRegionChangedEventArgs
ms.date: 02/26/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NonClientRegionChangedEventArgs
topic_type: 
- APIRef
api_name:
- ICoreWebView2NonClientRegionChangedEventArgs
- ICoreWebView2NonClientRegionChangedEventArgs.get_RegionKind
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2NonClientRegionChangedEventArgs

```
interface ICoreWebView2NonClientRegionChangedEventArgs
  : public IUnknown
```

This is the Interface for non-client region change event args.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_RegionKind](#get_regionkind) | This property represents the COREWEBVIEW2_NON_CLIENT_REGION_KIND which the region changed event corresponds to.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_RegionKind

This property represents the COREWEBVIEW2_NON_CLIENT_REGION_KIND which the region changed event corresponds to.

> public HRESULT [get_RegionKind](#get_regionkind)(COREWEBVIEW2_NON_CLIENT_REGION_KIND * value)

With this property an app can query for a collection of rects which have that region kind by using QueryNonClientRegion on the composition controller.

