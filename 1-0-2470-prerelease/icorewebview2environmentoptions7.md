---
description: Additional options used to create the WebView2 Environment that support specifying the `ReleaseChannels` and `ChannelSearchKind`.
title: WebView2 Win32 C++ ICoreWebView2EnvironmentOptions7
ms.date: 03/18/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2EnvironmentOptions7
topic_type: 
- APIRef
api_name:
- ICoreWebView2EnvironmentOptions7
- ICoreWebView2EnvironmentOptions7.get_ChannelSearchKind
- ICoreWebView2EnvironmentOptions7.get_ReleaseChannels
- ICoreWebView2EnvironmentOptions7.put_ChannelSearchKind
- ICoreWebView2EnvironmentOptions7.put_ReleaseChannels
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2EnvironmentOptions7

```
interface ICoreWebView2EnvironmentOptions7
  : public IUnknown
```

Additional options used to create the WebView2 Environment that support specifying the `ReleaseChannels` and `ChannelSearchKind`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ChannelSearchKind](#get_channelsearchkind) | Gets the `ChannelSearchKind` property.
[get_ReleaseChannels](#get_releasechannels) | Gets the `ReleaseChannels` property.
[put_ChannelSearchKind](#put_channelsearchkind) | The `ChannelSearchKind` property is `COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE` by default; environment creation searches for a release channel on the machine from most to least stable using the first channel found.
[put_ReleaseChannels](#put_releasechannels) | Sets the `ReleaseChannels`, which is a mask of one or more indicating which channels environment creation should search for.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_ChannelSearchKind

Gets the `ChannelSearchKind` property.

> public HRESULT [get_ChannelSearchKind](#get_channelsearchkind)(COREWEBVIEW2_CHANNEL_SEARCH_KIND * value)

#### get_ReleaseChannels

Gets the `ReleaseChannels` property.

> public HRESULT [get_ReleaseChannels](#get_releasechannels)(COREWEBVIEW2_RELEASE_CHANNELS * value)

#### put_ChannelSearchKind

The `ChannelSearchKind` property is `COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE` by default; environment creation searches for a release channel on the machine from most to least stable using the first channel found.

> public HRESULT [put_ChannelSearchKind](#put_channelsearchkind)(COREWEBVIEW2_CHANNEL_SEARCH_KIND value)

The default search order is: WebView2 Runtime -> Beta -> Dev -> Canary. Set `ChannelSearchKind` to `COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE` to reverse the search order so that environment creation searches for a channel from least to most stable. If `ReleaseChannels` has been provided, the loader will only search for channels in the set. See `COREWEBVIEW2_RELEASE_CHANNELS` for more details on channels.

This property can be overridden by the corresponding registry key `ChannelSearchKind` or the environment variable `WEBVIEW2_CHANNEL_SEARCH_KIND`. Set the value to `1` to set the search kind to `COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE`. See `CreateCoreWebView2EnvironmentWithOptions` for more details on overrides.

#### put_ReleaseChannels

Sets the `ReleaseChannels`, which is a mask of one or more indicating which channels environment creation should search for.

> public HRESULT [put_ReleaseChannels](#put_releasechannels)(COREWEBVIEW2_RELEASE_CHANNELS value)

OR operation(s) can be applied to multiple to create a mask. The default value is a mask of all the channels. By default, environment creation searches for channels from most to least stable, using the first channel found on the device. When is provided, environment creation will only search for the channels specified in the set. Set to to reverse the search order so that the loader searches for the least stable build first. See for descriptions of each channel. Environment creation fails if it is unable to find any channel from the installed on the device. Use to verify which channel is used. If both a and are provided, the takes precedence. The can be overridden by the corresponding registry override or the environment variable . Set the value to a comma-separated string of integers, which map to the values: Stable (0), Beta (1), Dev (2), and Canary (3). For example, the values "0,2" and "2,0" indicate that the loader should only search for Dev channel and the WebView2 Runtime, using the order indicated by . Environment creation attempts to interpret each integer and treats any invalid entry as Stable channel. 
ReleaseChannels   |Channel Search Kind: Most Stable (default)   |Channel Search Kind: Least Stable
--------- | --------- | ---------
CoreWebView2ReleaseChannels.Beta | CoreWebView2ReleaseChannels.Stable   |WebView2 Runtime -> Beta   |Beta -> WebView2 Runtime
CoreWebView2ReleaseChannels.Canary | CoreWebView2ReleaseChannels.Dev | CoreWebView2ReleaseChannels.Beta | CoreWebView2ReleaseChannels.Stable   |WebView2 Runtime -> Beta -> Dev -> Canary   |Canary -> Dev -> Beta -> WebView2 Runtime
CoreWebView2ReleaseChannels.Canary   |Canary   |Canary
CoreWebView2ReleaseChannels.Beta | CoreWebView2ReleaseChannels.Canary | CoreWebView2ReleaseChannels.Stable   |WebView2 Runtime -> Beta -> Canary   |Canary -> Beta -> WebView2 Runtime

