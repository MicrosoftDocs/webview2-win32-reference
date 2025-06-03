---
description: Additional options used to create WebView2 Environment to manage tracking prevention.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions5
ms.date: 05/27/2025
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
  : public IUnknown
```

Additional options used to create WebView2 Environment to manage tracking prevention.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_EnableTrackingPrevention](#get_enabletrackingprevention) | Gets the `EnableTrackingPrevention` property.
[put_EnableTrackingPrevention](#put_enabletrackingprevention) | The `EnableTrackingPrevention` property is used to enable/disable tracking prevention feature in WebView2.

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

The `EnableTrackingPrevention` property is used to enable/disable tracking prevention feature in WebView2.

> public HRESULT [put_EnableTrackingPrevention](#put_enabletrackingprevention)(BOOL value)

This property enable/disable tracking prevention for all the WebView2's created in the same environment. By default this feature is enabled to block potentially harmful trackers and trackers from sites that aren't visited before and set to `COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_BALANCED` or whatever value was last changed/persisted on the profile.

You can set this property to false to disable the tracking prevention feature if the app only renders content in the WebView2 that is known to be safe. Disabling this feature when creating environment also improves runtime performance by skipping related code.

You shouldn't disable this property if WebView2 is being used as a "full browser" with arbitrary navigation and should protect end user privacy.

There is `ICoreWebView2Profile3::PreferredTrackingPreventionLevel` property to control levels of tracking prevention of the WebView2's associated with a same profile. However, you can also disable tracking prevention later using `ICoreWebView2Profile3::PreferredTrackingPreventionLevel` property and `COREWEBVIEW2_TRACKING_PREVENTION_LEVEL_NONE` value but that doesn't improves runtime performance.

See `ICoreWebView2Profile3::PreferredTrackingPreventionLevel` for more details.

Tracking prevention protects users from online tracking by restricting the ability of trackers to access browser-based storage as well as the network. See [Tracking prevention](/microsoft-edge/web-platform/tracking-prevention).

