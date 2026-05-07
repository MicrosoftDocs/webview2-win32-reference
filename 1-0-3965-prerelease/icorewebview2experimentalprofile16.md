---
description: This is the ICoreWebView2Profile interface for origin feature management.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalProfile16
ms.date: 04/08/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalProfile16
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalProfile16
- ICoreWebView2ExperimentalProfile16.CreateOriginFeatureSetting
- ICoreWebView2ExperimentalProfile16.GetEffectiveFeaturesForOrigin
- ICoreWebView2ExperimentalProfile16.SetOriginFeatures
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalProfile16

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalProfile16
  : public IUnknown
```

This is the [ICoreWebView2Profile](icorewebview2profile.md#icorewebview2profile) interface for origin feature management.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[CreateOriginFeatureSetting](#createoriginfeaturesetting) | Creates a CoreWebView2OriginFeatureSetting objects.
[GetEffectiveFeaturesForOrigin](#geteffectivefeaturesfororigin) | Gets the effective feature settings for a specified origin.
[SetOriginFeatures](#setoriginfeatures) | Configures one or more feature settings for the specified origins.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### CreateOriginFeatureSetting

Creates a CoreWebView2OriginFeatureSetting objects.

> public HRESULT [CreateOriginFeatureSetting](#createoriginfeaturesetting)(COREWEBVIEW2_ORIGIN_FEATURE featureKind, COREWEBVIEW2_ORIGIN_FEATURE_STATE featureState, [ICoreWebView2ExperimentalOriginFeatureSetting](icorewebview2experimentaloriginfeaturesetting.md#icorewebview2experimentaloriginfeaturesetting) ** value)

This object represents a specific feature and its state (enabled or disabled). This method allows creating a feature settings object that can be used with SetOriginFeatures to configure features for origins.

#### GetEffectiveFeaturesForOrigin

Gets the effective feature settings for a specified origin.

> public HRESULT [GetEffectiveFeaturesForOrigin](#geteffectivefeaturesfororigin)(LPCWSTR origin, [ICoreWebView2ExperimentalGetEffectiveFeaturesForOriginCompletedHandler](icorewebview2experimentalgeteffectivefeaturesfororigincompletedhandler.md#icorewebview2experimentalgeteffectivefeaturesfororigincompletedhandler) * handler)

Returns a collection of feature settings for all the features in `COREWEBVIEW2_ORIGIN_FEATURE`. This collection contains the effective (computed) setting values for all features, including features that were not explicitly configured via `SetOriginFeatures` and thus have their default values. The order of features in the returned collection is not guaranteed. The origin should have a valid scheme and host (e.g. "https://www.example.com"), otherwise the method fails with `E_INVALIDARG`.

#### SetOriginFeatures

Configures one or more feature settings for the specified origins.

> public HRESULT [SetOriginFeatures](#setoriginfeatures)(UINT32 originsCount, LPCWSTR * originPatterns, UINT32 featureSettingsCount, [ICoreWebView2ExperimentalOriginFeatureSetting](icorewebview2experimentaloriginfeaturesetting.md#icorewebview2experimentaloriginfeaturesetting) ** featureSettings)

This method applies feature configurations such as enhanced security mode to origins. Origins may be provided as exact origin strings or as wildcard patterns.

The origin pattern can be an exact origin string or a wildcard pattern. For wildcard patterns, `*` matches zero or more characters. Examples: 
Origin Filter String   |What It Matches   |Description
--------- | --------- | ---------
`https://contoso.com`|Only `https://contoso.com`|Matches the exact origin with specific protocol and hostname
`https://[*.]contoso.com`|`https://app.contoso.com`,`https://api.contoso.com`,`https://admin.contoso.com`|Matches any subdomain under the specified domain
`*://contoso.com`|`https://contoso.com`,`http://contoso.com`,`ftp://contoso.com`|Matches any protocol for the specified hostname
`https://www.microsoft.com:*`|`https://www.microsoft.com:123`|Matches any port for the specified origin
`[*.]example.com`|`https://www.example.com`,`http://abc.example.com`|Matches any subdomain with any protocol for the specified domain
`https://xn--qei.example/`|`https://??????.example/`,`https://xn--qei.example/`|Normalized punycode matches with corresponding Non-ASCII hostnames

Calling this method multiple times with the same (featureKind, featureState) pair overwrites the previous configuration; the most recent call takes precedence.

When multiple configurations exist for the same feature but specify different featureState values, the configuration whose origin pattern is more specific takes precedence.

The specificity of an origin pattern is determined by the presence and placement of wildcards. Three wildcard categories influence specificity:

* Wildcards in the port (for example, `https://www.example.com:*&zwj;/*`)

* Wildcards in the scheme (for example, `*://www.example.com:123/*`)

* Wildcards in the hostname (for example, `https://*.example.com:123/*`)

If one pattern is more specific in one component but less specific in another, specificity is evaluated in the following order:

1. Hostname

1. Scheme

1. Port

For example, the following patterns are ordered by precedence: `https://www.example.com:*&zwj;/*` ???????? `*://www.example.com:123/*` ???????? `https://*.example.com:123/*`.

To reset the origin list for a particular (feature, state) pair, call `SetOriginFeatures` with an empty origin list or nullptr for the same feature setting. For example, 
```
SetOriginFeatures(1, {"https://microsoft.com"}, 1, {{ESM: Enabled}});
SetOriginFeatures(0, {}, 1, {{ESM: Enabled}}); // Resets {ESM: Enabled}
```

