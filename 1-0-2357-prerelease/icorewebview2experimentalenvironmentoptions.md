---
description: Additional options used to create the WebView2 Environment that support specifying the `ReleaseChannels` and `ChannelSearchKind`.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalEnvironmentOptions
ms.date: 01/23/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalEnvironmentOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalEnvironmentOptions
- ICoreWebView2ExperimentalEnvironmentOptions.get_ChannelSearchKind
- ICoreWebView2ExperimentalEnvironmentOptions.get_ReleaseChannels
- ICoreWebView2ExperimentalEnvironmentOptions.put_ChannelSearchKind
- ICoreWebView2ExperimentalEnvironmentOptions.put_ReleaseChannels
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalEnvironmentOptions

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalEnvironmentOptions
  : public IUnknown
```

Additional options used to create the WebView2 Environment that support specifying the `ReleaseChannels` and `ChannelSearchKind`.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_ChannelSearchKind](#get_channelsearchkind) | The `ChannelSearchKind` property is `COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE` by default; environment creation searches for a release channel on the machine from most to least stable using the first channel found.
[get_ReleaseChannels](#get_releasechannels) | Gets the `ReleaseChannels`.
[put_ChannelSearchKind](#put_channelsearchkind) | Sets the `ChannelSearchKind` property.
[put_ReleaseChannels](#put_releasechannels) | Sets the `ReleaseChannels`, which is a mask of one or more `COREWEBVIEW2_RELEASE_CHANNELS`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    0.9.579

## Members

#### get_ChannelSearchKind

The `ChannelSearchKind` property is `COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE` by default; environment creation searches for a release channel on the machine from most to least stable using the first channel found.

> public HRESULT [get_ChannelSearchKind](#get_channelsearchkind)(COREWEBVIEW2_CHANNEL_SEARCH_KIND * value)

The default search order is: WebView2 Runtime -> Beta -> Dev -> Canary. Set `ChannelSearchKind` to `COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE` to reverse the search order so that environment creation searches for a channel from least to most stable. If `ReleaseChannels` has been provided, the loader will only search for channels in the set. See `COREWEBVIEW2_RELEASE_CHANNELS` for more details on channels.

This property can be overridden by the corresponding registry key `ChannelSearchKind` or the environment variable `WEBVIEW2_CHANNEL_SEARCH_KIND`. Set the value to `1` to set the search kind to `COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE`. See `CreateCoreWebView2EnvironmentWithOptions` for more details on overrides.

#### get_ReleaseChannels

Gets the `ReleaseChannels`.

> public HRESULT [get_ReleaseChannels](#get_releasechannels)(COREWEBVIEW2_RELEASE_CHANNELS * value)

#### put_ChannelSearchKind

Sets the `ChannelSearchKind` property.

> public HRESULT [put_ChannelSearchKind](#put_channelsearchkind)(COREWEBVIEW2_CHANNEL_SEARCH_KIND value)

#### put_ReleaseChannels

Sets the `ReleaseChannels`, which is a mask of one or more `COREWEBVIEW2_RELEASE_CHANNELS`.

> public HRESULT [put_ReleaseChannels](#put_releasechannels)(COREWEBVIEW2_RELEASE_CHANNELS value)

OR operation(s) can be applied to multiple `COREWEBVIEW2_RELEASE_CHANNELS` to create a mask. The default value is a a mask of all the channels. By default, environment creation searches for channels from most to least stable, using the first channel found on the device. When `ReleaseChannels` is provided, environment creation will only search for the channels specified in the set. Set `ChannelSearchKind` to `COREWEBVIEW2_CHANNEL_SEARCH_KIND_LEAST_STABLE` to reverse the search order so environment creation searches for least stable build first. See `COREWEBVIEW2_RELEASE_CHANNELS` for descriptions of each channel.

`CreateCoreWebView2EnvironmentWithOptions` fails with `HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)` if environment creation is unable to find any channel from the `ReleaseChannels` installed on the device. Use `GetAvailableCoreWebView2BrowserVersionStringWithOptions` on [ICoreWebView2Environment](icorewebview2environment.md) to verify which channel is used when this option is set.

Examples: 
ReleaseChannels   |Channel Search Kind: Most Stable (default)   |Channel Search Kind: Least Stable
--------- | --------- | ---------
COREWEBVIEW2_RELEASE_CHANNELS_BETA | COREWEBVIEW2_RELEASE_CHANNELS_STABLE   |WebView2 Runtime -> Beta   |Beta -> WebView2 Runtime
COREWEBVIEW2_RELEASE_CHANNELS_CANARY | COREWEBVIEW2_RELEASE_CHANNELS_DEV | COREWEBVIEW2_RELEASE_CHANNELS_BETA | COREWEBVIEW2_RELEASE_CHANNELS_STABLE   |WebView2 Runtime -> Beta -> Dev -> Canary   |Canary -> Dev -> Beta -> WebView2 Runtime
COREWEBVIEW2_RELEASE_CHANNELS_CANARY   |Canary   |Canary
COREWEBVIEW2_RELEASE_CHANNELS_BETA | COREWEBVIEW2_RELEASE_CHANNELS_CANARY | COREWEBVIEW2_RELEASE_CHANNELS_STABLE   |WebView2 Runtime -> Beta -> Canary   |Canary -> Beta -> WebView2 Runtime

If both `BrowserExecutableFolder` and `ReleaseChannels` are provided, the `BrowserExecutableFolder` takes precedence, regardless of whether or not the channel of `BrowserExecutableFolder` is included in the `releaseChannels`. `ReleaseChannels` can be overridden by the corresponding registry override `ReleaseChannels` or the environment variable `WEBVIEW2_RELEASE_CHANNELS`. Set the value to a comma-separated string of integers, which map to the `COREWEBVIEW2_RELEASE_CHANNELS` values: Stable (0), Beta (1), Dev (2), and Canary (3). For example, the values "0,2" and "2,0" indicate that environment creation should only search for Dev channel and the WebView2 Runtime, using the order indicated by `ChannelSearchKind`. Environment creation attempts to interpret each integer and treats any invalid entry as Stable channel. See `CreateCoreWebView2EnvironmentWithOptions` for more details on overrides.

