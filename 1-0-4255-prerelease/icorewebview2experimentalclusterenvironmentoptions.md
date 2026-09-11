---
description: The options used to establish or attach to a shared WebView2 cluster environment.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalClusterEnvironmentOptions
ms.date: 09/03/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalClusterEnvironmentOptions
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalClusterEnvironmentOptions
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_AdditionalBrowserArguments
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_AllowSingleSignOnUsingOSPrimaryAccount
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_AreBrowserExtensionsEnabled
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_ChannelSearchKind
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_ClusterName
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_EnableTrackingPrevention
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_Language
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_PerHostProfileIsolation
- ICoreWebView2ExperimentalClusterEnvironmentOptions.get_ReleaseChannels
- ICoreWebView2ExperimentalClusterEnvironmentOptions.GetCustomSchemeRegistrations
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_AdditionalBrowserArguments
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_AllowSingleSignOnUsingOSPrimaryAccount
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_AreBrowserExtensionsEnabled
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_ChannelSearchKind
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_ClusterName
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_EnableTrackingPrevention
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_Language
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_PerHostProfileIsolation
- ICoreWebView2ExperimentalClusterEnvironmentOptions.put_ReleaseChannels
- ICoreWebView2ExperimentalClusterEnvironmentOptions.SetCustomSchemeRegistrations
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalClusterEnvironmentOptions

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalClusterEnvironmentOptions
  : public IUnknown
```

The options used to establish or attach to a shared WebView2 cluster environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalBrowserArguments](#get_additionalbrowserarguments) | Gets the `AdditionalBrowserArguments` property.
[get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount) | Gets the `AllowSingleSignOnUsingOSPrimaryAccount` property.
[get_AreBrowserExtensionsEnabled](#get_arebrowserextensionsenabled) | Gets the `AreBrowserExtensionsEnabled` property.
[get_ChannelSearchKind](#get_channelsearchkind) | Gets the `ChannelSearchKind` property.
[get_ClusterName](#get_clustername) | Gets the `ClusterName` property.
[get_EnableTrackingPrevention](#get_enabletrackingprevention) | Gets the `EnableTrackingPrevention` property.
[get_Language](#get_language) | Gets the `Language` property.
[get_PerHostProfileIsolation](#get_perhostprofileisolation) | Gets the `PerHostProfileIsolation` property.
[get_ReleaseChannels](#get_releasechannels) | Gets the `ReleaseChannels` property.
[GetCustomSchemeRegistrations](#getcustomschemeregistrations) | Gets the custom scheme registrations that are part of the pinned set.
[put_AdditionalBrowserArguments](#put_additionalbrowserarguments) | Additional command-line switches passed to the shared browser process.
[put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount) | Whether single sign on using the OS primary account is allowed for the shared environment.
[put_AreBrowserExtensionsEnabled](#put_arebrowserextensionsenabled) | Whether browser extensions are enabled for the shared environment.
[put_ChannelSearchKind](#put_channelsearchkind) | The `ChannelSearchKind` determines the order that release channels are searched for during shared environment creation.
[put_ClusterName](#put_clustername) | The rendezvous name that identifies the cluster.
[put_EnableTrackingPrevention](#put_enabletrackingprevention) | Whether tracking prevention is enabled for the shared environment.
[put_Language](#put_language) | The default display language for the shared environment.
[put_PerHostProfileIsolation](#put_perhostprofileisolation) | When `TRUE` (the default), the effective profile name is namespaced per host application, using the pattern `HostName_ProfileName`, to prevent accidental cross-app profile use.
[put_ReleaseChannels](#put_releasechannels) | The `ReleaseChannels` is a mask of one or more `COREWEBVIEW2_RELEASE_CHANNELS` indicating which channels the shared environment creation should search for.
[SetCustomSchemeRegistrations](#setcustomschemeregistrations) | Sets the custom scheme registrations that are part of the pinned set.

A "cluster" is a WebView2 environment that a group of cooperating host applications deliberately share, identified by a well-known `ClusterName` string that those hosts agree on out of band.

Only options that can be shared process-wide across cooperating hosts are present. Options that cannot hold a single value across a shared browser process tree (for example the remote-debugging port or logging) are intentionally omitted, so a host cannot set something on a cluster that would silently be ignored. The first host to establish a cluster for a given `ClusterName` (when no browser is running for it) pins these options for as long as the cluster's browser process stays alive; once that browser exits the pinned set no longer applies and the next host may pin a different set.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### get_AdditionalBrowserArguments

Gets the `AdditionalBrowserArguments` property.

> public HRESULT [get_AdditionalBrowserArguments](#get_additionalbrowserarguments)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_AllowSingleSignOnUsingOSPrimaryAccount

Gets the `AllowSingleSignOnUsingOSPrimaryAccount` property.

> public HRESULT [get_AllowSingleSignOnUsingOSPrimaryAccount](#get_allowsinglesignonusingosprimaryaccount)(BOOL * value)

#### get_AreBrowserExtensionsEnabled

Gets the `AreBrowserExtensionsEnabled` property.

> public HRESULT [get_AreBrowserExtensionsEnabled](#get_arebrowserextensionsenabled)(BOOL * value)

#### get_ChannelSearchKind

Gets the `ChannelSearchKind` property.

> public HRESULT [get_ChannelSearchKind](#get_channelsearchkind)(COREWEBVIEW2_CHANNEL_SEARCH_KIND * value)

#### get_ClusterName

Gets the `ClusterName` property.

> public HRESULT [get_ClusterName](#get_clustername)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_EnableTrackingPrevention

Gets the `EnableTrackingPrevention` property.

> public HRESULT [get_EnableTrackingPrevention](#get_enabletrackingprevention)(BOOL * value)

#### get_Language

Gets the `Language` property.

> public HRESULT [get_Language](#get_language)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_PerHostProfileIsolation

Gets the `PerHostProfileIsolation` property.

> public HRESULT [get_PerHostProfileIsolation](#get_perhostprofileisolation)(BOOL * value)

#### get_ReleaseChannels

Gets the `ReleaseChannels` property.

> public HRESULT [get_ReleaseChannels](#get_releasechannels)(COREWEBVIEW2_RELEASE_CHANNELS * value)

#### GetCustomSchemeRegistrations

Gets the custom scheme registrations that are part of the pinned set.

> public HRESULT [GetCustomSchemeRegistrations](#getcustomschemeregistrations)(UINT32 * count, [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md#icorewebview2customschemeregistration) *** schemeRegistrations)

The returned [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md#icorewebview2customschemeregistration) pointers must be released, and the array itself must be deallocated with `CoTaskMemFree`.

#### put_AdditionalBrowserArguments

Additional command-line switches passed to the shared browser process.

> public HRESULT [put_AdditionalBrowserArguments](#put_additionalbrowserarguments)(LPCWSTR value)

Because the process is shared, this value is part of the pinned set and is process-wide. See `ICoreWebView2EnvironmentOptions.AdditionalBrowserArguments` for the accepted format and the switches that are ignored.

#### put_AllowSingleSignOnUsingOSPrimaryAccount

Whether single sign on using the OS primary account is allowed for the shared environment.

> public HRESULT [put_AllowSingleSignOnUsingOSPrimaryAccount](#put_allowsinglesignonusingosprimaryaccount)(BOOL value)

See `ICoreWebView2EnvironmentOptions.AllowSingleSignOnUsingOSPrimaryAccount`. The default is `FALSE`.

#### put_AreBrowserExtensionsEnabled

Whether browser extensions are enabled for the shared environment.

> public HRESULT [put_AreBrowserExtensionsEnabled](#put_arebrowserextensionsenabled)(BOOL value)

See `ICoreWebView2EnvironmentOptions6.AreBrowserExtensionsEnabled`. The default is `FALSE`.

#### put_ChannelSearchKind

The `ChannelSearchKind` determines the order that release channels are searched for during shared environment creation.

> public HRESULT [put_ChannelSearchKind](#put_channelsearchkind)(COREWEBVIEW2_CHANNEL_SEARCH_KIND value)

See `ICoreWebView2EnvironmentOptions8.ChannelSearchKind`. Because the browser process is shared, this value is part of the pinned set. The default is `COREWEBVIEW2_CHANNEL_SEARCH_KIND_MOST_STABLE`.

#### put_ClusterName

The rendezvous name that identifies the cluster.

> public HRESULT [put_ClusterName](#put_clustername)(LPCWSTR value)

All cooperating hosts agree on this value out of band. To avoid colliding with another application's cluster, include a name you control, such as your company or product name, or a GUID. Must not be null or empty.

Because the `ClusterName` is mapped to an on-disk user data folder, it is treated as a case-insensitive name, is limited to 64 characters, and must be a valid file-system folder name: it cannot contain path separators or characters that are invalid in a folder name. An invalid `ClusterName` fails the call with `E_INVALIDARG`.

#### put_EnableTrackingPrevention

Whether tracking prevention is enabled for the shared environment.

> public HRESULT [put_EnableTrackingPrevention](#put_enabletrackingprevention)(BOOL value)

See `ICoreWebView2EnvironmentOptions5.EnableTrackingPrevention`. The default is `TRUE`.

#### put_Language

The default display language for the shared environment.

> public HRESULT [put_Language](#put_language)(LPCWSTR value)

It applies to browser UI such as context menus and dialogs, and to the `accept-languages` HTTP header. The value is in the format of BCP 47 Language Tags.

#### put_PerHostProfileIsolation

When `TRUE` (the default), the effective profile name is namespaced per host application, using the pattern `HostName_ProfileName`, to prevent accidental cross-app profile use.

> public HRESULT [put_PerHostProfileIsolation](#put_perhostprofileisolation)(BOOL value)

This is anti-misuse, not a security boundary: it does not encrypt or ACL profile data, and any app that knows the cluster `ClusterName` and profile name can use a shared profile. The naming is deliberately OS-neutral: `HostName` is the host application identity on the current platform (the executable name on Windows).

#### put_ReleaseChannels

The `ReleaseChannels` is a mask of one or more `COREWEBVIEW2_RELEASE_CHANNELS` indicating which channels the shared environment creation should search for.

> public HRESULT [put_ReleaseChannels](#put_releasechannels)(COREWEBVIEW2_RELEASE_CHANNELS value)

See `ICoreWebView2EnvironmentOptions8.ReleaseChannels`. Because the browser process is shared, this value is part of the pinned set and selects the channel of the shared browser. The default is a mask of all channels.

#### SetCustomSchemeRegistrations

Sets the custom scheme registrations that are part of the pinned set.

> public HRESULT [SetCustomSchemeRegistrations](#setcustomschemeregistrations)(UINT32 count, [ICoreWebView2CustomSchemeRegistration](icorewebview2customschemeregistration.md#icorewebview2customschemeregistration) ** schemeRegistrations)

