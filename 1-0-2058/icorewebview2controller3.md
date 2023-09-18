---
description: 
title: WebView2 Win32 C++ ICoreWebView2Controller3
ms.date: 09/08/2023
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Controller3
topic_type: 
- APIRef
api_name:
- ICoreWebView2Controller3
- ICoreWebView2Controller3.add_RasterizationScaleChanged
- ICoreWebView2Controller3.get_BoundsMode
- ICoreWebView2Controller3.get_RasterizationScale
- ICoreWebView2Controller3.get_ShouldDetectMonitorScaleChanges
- ICoreWebView2Controller3.put_BoundsMode
- ICoreWebView2Controller3.put_RasterizationScale
- ICoreWebView2Controller3.put_ShouldDetectMonitorScaleChanges
- ICoreWebView2Controller3.remove_RasterizationScaleChanged
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Controller3

```
interface ICoreWebView2Controller3
  : public ICoreWebView2Controller2
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_RasterizationScaleChanged](#add_rasterizationscalechanged) | Adds an event handler for the `RasterizationScaleChanged` event.
[get_BoundsMode](#get_boundsmode) | Gets the `BoundsMode` property.
[get_RasterizationScale](#get_rasterizationscale) | Gets the `RasterizationScale` property.
[get_ShouldDetectMonitorScaleChanges](#get_shoulddetectmonitorscalechanges) | Gets the `ShouldDetectMonitorScaleChanges` property.
[put_BoundsMode](#put_boundsmode) | Sets the `BoundsMode` property.
[put_RasterizationScale](#put_rasterizationscale) | Sets the `RasterizationScale` property.
[put_ShouldDetectMonitorScaleChanges](#put_shoulddetectmonitorscalechanges) | Sets the `ShouldDetectMonitorScaleChanges` property.
[remove_RasterizationScaleChanged](#remove_rasterizationscalechanged) | Removes an event handler previously added with `add_RasterizationScaleChanged`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.774.44
WebView2 Win32 Prerelease |    1.0.824

## Members

#### add_RasterizationScaleChanged

Adds an event handler for the `RasterizationScaleChanged` event.

> public HRESULT [add_RasterizationScaleChanged](#add_rasterizationscalechanged)([ICoreWebView2RasterizationScaleChangedEventHandler](icorewebview2rasterizationscalechangedeventhandler.md) * eventHandler, EventRegistrationToken * token)

#### get_BoundsMode

Gets the `BoundsMode` property.

> public HRESULT [get_BoundsMode](#get_boundsmode)(COREWEBVIEW2_BOUNDS_MODE * value)

#### get_RasterizationScale

Gets the `RasterizationScale` property.

> public HRESULT [get_RasterizationScale](#get_rasterizationscale)(double * value)

#### get_ShouldDetectMonitorScaleChanges

Gets the `ShouldDetectMonitorScaleChanges` property.

> public HRESULT [get_ShouldDetectMonitorScaleChanges](#get_shoulddetectmonitorscalechanges)(BOOL * value)

#### put_BoundsMode

Sets the `BoundsMode` property.

> public HRESULT [put_BoundsMode](#put_boundsmode)(COREWEBVIEW2_BOUNDS_MODE value)

#### put_RasterizationScale

Sets the `RasterizationScale` property.

> public HRESULT [put_RasterizationScale](#put_rasterizationscale)(double value)

#### put_ShouldDetectMonitorScaleChanges

Sets the `ShouldDetectMonitorScaleChanges` property.

> public HRESULT [put_ShouldDetectMonitorScaleChanges](#put_shoulddetectmonitorscalechanges)(BOOL value)

#### remove_RasterizationScaleChanged

Removes an event handler previously added with `add_RasterizationScaleChanged`.

> public HRESULT [remove_RasterizationScaleChanged](#remove_rasterizationscalechanged)(EventRegistrationToken token)

