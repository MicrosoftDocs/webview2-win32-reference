---
description: Represents the registration of a custom scheme with the CoreWebView2Environment.
title: WebView2 Win32 C++ ICoreWebView2CustomSchemeRegistration
ms.date: 07/08/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CustomSchemeRegistration
topic_type: 
- APIRef
api_name:
- ICoreWebView2CustomSchemeRegistration
- ICoreWebView2CustomSchemeRegistration.get_HasAuthorityComponent
- ICoreWebView2CustomSchemeRegistration.get_SchemeName
- ICoreWebView2CustomSchemeRegistration.get_TreatAsSecure
- ICoreWebView2CustomSchemeRegistration.GetAllowedOrigins
- ICoreWebView2CustomSchemeRegistration.put_HasAuthorityComponent
- ICoreWebView2CustomSchemeRegistration.put_TreatAsSecure
- ICoreWebView2CustomSchemeRegistration.SetAllowedOrigins
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CustomSchemeRegistration

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2CustomSchemeRegistration
  : public IUnknown
```

Represents the registration of a custom scheme with the CoreWebView2Environment.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_HasAuthorityComponent](#get_hasauthoritycomponent) | Set this property to `true` if the URIs with this custom scheme will have an authority component (a host for custom schemes).
[get_SchemeName](#get_schemename) | The name of the custom scheme to register.
[get_TreatAsSecure](#get_treatassecure) | Whether the sites with this scheme will be treated as a [Secure Context](https://developer.mozilla.org/docs/Web/Security/Secure_Contexts) like an HTTPS site.
[GetAllowedOrigins](#getallowedorigins) | List of origins that are allowed to issue requests with the custom scheme, such as XHRs and subresource requests that have an Origin header.
[put_HasAuthorityComponent](#put_hasauthoritycomponent) | Get has authority component.
[put_TreatAsSecure](#put_treatassecure) | Set if the scheme will be treated as a Secure Context.
[SetAllowedOrigins](#setallowedorigins) | Set the array of origins that are allowed to use the scheme.

This allows the WebView2 app to be able to handle WebResourceRequested event for requests with the specified scheme and be able to navigate the WebView2 to the custom scheme. Once the environment is created, the registrations are valid and immutable throughout the lifetime of the associated WebView2s' browser process and any WebView2 environments sharing the browser process must be created with identical custom scheme registrations, otherwise the environment creation will fail. Any further attempts to register the same scheme will fail during environment creation. The URIs of registered custom schemes will be treated similar to http URIs for their origins. They will have tuple origins for URIs with host and opaque origins for URIs without host as specified in [7.5 Origin - HTML Living Standard](https://html.spec.whatwg.org/multipage/origin.html)

Example: `custom-scheme-with-host://hostname/path/to/resource` has origin of `custom-scheme-with-host://hostname`. `custom-scheme-without-host:path/to/resource` has origin of `custom-scheme-without-host:path/to/resource`. For WebResourceRequested event, the cases of request URIs and filter URIs with custom schemes will be normalized according to generic URI syntax rules. Any non-ASCII characters will be preserved. The registered custom schemes also participate in [CORS](https://developer.mozilla.org/docs/Web/HTTP/CORS) and adheres to [CSP](https://developer.mozilla.org/docs/Web/HTTP/CSP). The app needs to set the appropriate access headers in its WebResourceRequested event handler to allow CORS requests. 
```cpp
    Microsoft::WRL::ComPtr<ICoreWebView2EnvironmentOptions4> options4;
    if (options.As(&options4) == S_OK)
    {
        const WCHAR* allowedOrigins[1] = {L"https://*.example.com"};

        auto customSchemeRegistration =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"custom-scheme");
        customSchemeRegistration->SetAllowedOrigins(1, allowedOrigins);
        auto customSchemeRegistration2 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(L"wv2rocks");
        customSchemeRegistration2->put_TreatAsSecure(TRUE);
        customSchemeRegistration2->SetAllowedOrigins(1, allowedOrigins);
        customSchemeRegistration2->put_HasAuthorityComponent(TRUE);
        auto customSchemeRegistration3 =
            Microsoft::WRL::Make<CoreWebView2CustomSchemeRegistration>(
                L"custom-scheme-not-in-allowed-origins");
        ICoreWebView2CustomSchemeRegistration* registrations[3] = {
            customSchemeRegistration.Get(), customSchemeRegistration2.Get(),
            customSchemeRegistration3.Get()};
        options4->SetCustomSchemeRegistrations(
            2, static_cast<ICoreWebView2CustomSchemeRegistration**>(registrations));
    }
```

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1587.40
WebView2 Win32 Prerelease |    1.0.1619

## Members

#### get_HasAuthorityComponent

Set this property to `true` if the URIs with this custom scheme will have an authority component (a host for custom schemes).

> public HRESULT [get_HasAuthorityComponent](#get_hasauthoritycomponent)(BOOL * hasAuthorityComponent)

Specifically, if you have a URI of the following form you should set the `HasAuthorityComponent` value as listed.

URI   |Recommended HasAuthorityComponent value
--------- | ---------
`custom-scheme-with-authority://host/path`|`true`
`custom-scheme-without-authority:path`|`false`

When this property is set to `true`, the URIs with this scheme will be interpreted as having a [scheme and host](https://html.spec.whatwg.org/multipage/origin.html#concept-origin-tuple) origin similar to an http URI. Note that the port and user information are never included in the computation of origins for custom schemes. If this property is set to `false`, URIs with this scheme will have an [opaque origin](https://html.spec.whatwg.org/multipage/origin.html#concept-origin-opaque) similar to a data URI. This property is `false` by default.

Note: For custom schemes registered as having authority component, navigations to URIs without authority of such custom schemes will fail. However, if the content inside WebView2 references a subresource with a URI that does not have an authority component, but of a custom scheme that is registered as having authority component, the URI will be interpreted as a relative path as specified in [RFC3986](https://www.rfc-editor.org/rfc/rfc3986). For example, `custom-scheme-with-authority:path` will be interpreted as `custom-scheme-with-authority://host/path`. However, this behavior cannot be guaranteed to remain in future releases so it is recommended not to rely on this behavior.

#### get_SchemeName

The name of the custom scheme to register.

> public HRESULT [get_SchemeName](#get_schemename)(LPWSTR * schemeName)

#### get_TreatAsSecure

Whether the sites with this scheme will be treated as a [Secure Context](https://developer.mozilla.org/docs/Web/Security/Secure_Contexts) like an HTTPS site.

> public HRESULT [get_TreatAsSecure](#get_treatassecure)(BOOL * treatAsSecure)

This flag is only effective when HasAuthorityComponent is also set to `true`. `false` by default.

#### GetAllowedOrigins

List of origins that are allowed to issue requests with the custom scheme, such as XHRs and subresource requests that have an Origin header.

> public HRESULT [GetAllowedOrigins](#getallowedorigins)(UINT32 * allowedOriginsCount, LPWSTR ** allowedOrigins)

The origin of any request (requests that have the [Origin header](https://developer.mozilla.org/docs/Web/HTTP/Headers/Origin)) to the custom scheme URI needs to be in this list. No-origin requests are requests that do not have an Origin header, such as link navigations, embedded images and are always allowed. Note: POST requests always contain an Origin header, therefore AllowedOrigins must be set for even for same origin POST requests. Note that cross-origin restrictions still apply. From any opaque origin (Origin header is null), no cross-origin requests are allowed. If the list is empty, no cross-origin request to this scheme is allowed. Origins are specified as a string in the format of scheme://host:port. The origins are string pattern matched with `*` (matches 0 or more characters) and `?` (matches 0 or 1 character) wildcards just like the URI matching in the [AddWebResourceRequestedFilter API](/dotnet/api/microsoft.web.webview2.core.corewebview2.addwebresourcerequestedfilter). For example, "http://*.example.com:80". Here's a set of examples of what is allowed and not:

Request URI   |Originating URL   |AllowedOrigins   |Allowed
--------- | --------- | --------- | ---------
`custom-scheme:request`|`https://www.example.com`|{"https://www.example.com"}   |Yes
`custom-scheme:request`|`https://www.example.com`|{"https://*.example.com"}   |Yes
`custom-scheme:request`|`https://www.example.com`|{"https://www.example2.com"}   |No
`custom-scheme-with-authority://host/path`|`custom-scheme-with-authority://host2`|{""}   |No
`custom-scheme-with-authority://host/path`|`custom-scheme-with-authority2://host`|{"custom-scheme-with-authority2://*"}   |Yes
`custom-scheme-without-authority:path`|custom-scheme-without-authority:path2   |{"custom-scheme-without-authority:*"}   |No
`custom-scheme-without-authority:path`|custom-scheme-without-authority:path2   |{"*"}   |Yes

The returned strings and the array itself must be deallocated with CoTaskMemFree.

#### put_HasAuthorityComponent

Get has authority component.

> public HRESULT [put_HasAuthorityComponent](#put_hasauthoritycomponent)(BOOL hasAuthorityComponent)

#### put_TreatAsSecure

Set if the scheme will be treated as a Secure Context.

> public HRESULT [put_TreatAsSecure](#put_treatassecure)(BOOL value)

#### SetAllowedOrigins

Set the array of origins that are allowed to use the scheme.

> public HRESULT [SetAllowedOrigins](#setallowedorigins)(UINT32 allowedOriginsCount, LPCWSTR * allowedOrigins)

