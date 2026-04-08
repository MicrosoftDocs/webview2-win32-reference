---
description: Represents a feature setting configuration for an origin.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalOriginFeatureSetting
ms.date: 04/08/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalOriginFeatureSetting
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalOriginFeatureSetting
- ICoreWebView2ExperimentalOriginFeatureSetting.get_Feature
- ICoreWebView2ExperimentalOriginFeatureSetting.get_State
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalOriginFeatureSetting

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalOriginFeatureSetting
  : public IUnknown
```

Represents a feature setting configuration for an origin.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_Feature](#get_feature) | The feature type for this setting.
[get_State](#get_state) | Indicates whether the feature is enabled for the origin.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_Feature

The feature type for this setting.

> public HRESULT [get_Feature](#get_feature)(COREWEBVIEW2_ORIGIN_FEATURE * value)

#### get_State

Indicates whether the feature is enabled for the origin.

> public HRESULT [get_State](#get_state)(COREWEBVIEW2_ORIGIN_FEATURE_STATE * value)

