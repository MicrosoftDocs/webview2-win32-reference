---
description: This interface is an extension of ICoreWebView2 that allows to set filters in order to receive WebResourceRequested events for service workers, shared workers and different origin iframes.
title: WebView2 Win32 C++ ICoreWebView2_22
ms.date: 02/20/2024
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_22
topic_type: 
- APIRef
api_name:
- ICoreWebView2_22
- ICoreWebView2_22.AddWebResourceRequestedFilterWithRequestSourceKinds
- ICoreWebView2_22.RemoveWebResourceRequestedFilterWithRequestSourceKinds
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_22

```
interface ICoreWebView2_22
  : public ICoreWebView2_21
```

This interface is an extension of [ICoreWebView2](icorewebview2.md) that allows to set filters in order to receive WebResourceRequested events for service workers, shared workers and different origin iframes.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[AddWebResourceRequestedFilterWithRequestSourceKinds](#addwebresourcerequestedfilterwithrequestsourcekinds) | A web resource request with a resource context that matches this filter's resource context and a URI that matches this filter's URI wildcard string for corresponding request sources will be raised via the `WebResourceRequested` event.
[RemoveWebResourceRequestedFilterWithRequestSourceKinds](#removewebresourcerequestedfilterwithrequestsourcekinds) | Removes a matching WebResource filter that was previously added for the `WebResourceRequested` event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.2357

## Members

#### AddWebResourceRequestedFilterWithRequestSourceKinds

A web resource request with a resource context that matches this filter's resource context and a URI that matches this filter's URI wildcard string for corresponding request sources will be raised via the `WebResourceRequested` event.

> public HRESULT [AddWebResourceRequestedFilterWithRequestSourceKinds](#addwebresourcerequestedfilterwithrequestsourcekinds)(LPCWSTR const uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT const resourceContext, COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS const requestSourceKinds)

To receive all raised events filters have to be added before main page navigation.

The `uri` parameter value is a wildcard string matched against the URI of the web resource request. This is a glob style wildcard string in which a `*` matches zero or more characters and a `?` matches exactly one character. These wildcard characters can be escaped using a backslash just before the wildcard character in order to represent the literal `*` or `?`.

The matching occurs over the URI as a whole string and not limiting wildcard matches to particular parts of the URI. The wildcard filter is compared to the URI after the URI has been normalized, any URI fragment has been removed, and non-ASCII hostnames have been converted to punycode.

Specifying a `nullptr` for the uri is equivalent to an empty string which matches no URIs.

For more information about resource context filters, navigate to [COREWEBVIEW2_WEB_RESOURCE_CONTEXT](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_web_resource_context).

The `requestSourceKinds` is a mask of one or more `COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS`. OR operation(s) can be applied to multiple `COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS` to create a mask representing those data types. API returns `E_INVALIDARG` if `requestSourceKinds` equals to zero. For more information about request source kinds, navigate to [COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS](/microsoft-edge/webview2/reference/win32/icorewebview2#corewebview2_web_resource_request_source_kinds).

Because service workers and shared workers run separately from any one HTML document their WebResourceRequested will be raised for all CoreWebView2s that have appropriate filters added in the corresponding CoreWebView2Environment. You should only add a WebResourceRequested filter for COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SERVICE_WORKER or COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SHARED_WORKER on one CoreWebView2 to avoid handling the same WebResourceRequested event multiple times.

URI Filter String   |Request URI   |Match   |Notes
--------- | --------- | --------- | ---------
`*`|`https://contoso.com/a/b/c`|Yes   |A single * will match all URIs
`*://contoso.com/*`|`https://contoso.com/a/b/c`|Yes   |Matches everything in contoso.com across all schemes
`*://contoso.com/*`|`https://example.com/?https://contoso.com/`|Yes   |But also matches a URI with just the same text anywhere in the URI
`example`|`https://contoso.com/example`|No   |The filter does not perform partial matches
`*example`|`https://contoso.com/example`|Yes   |The filter matches across URI parts
`*example`|`https://contoso.com/path/?example`|Yes   |The filter matches across URI parts
`*example`|`https://contoso.com/path/?query#example`|No   |The filter is matched against the URI with no fragment
`*example`|`https://example`|No   |The URI is normalized before filter matching so the actual URI used for comparison is `https://example/`
`*example/`|`https://example`|Yes   |Just like above, but this time the filter ends with a / just like the normalized URI
`https://xn--qei.example/`|`https://&#x2764;.example/`|Yes   |Non-ASCII hostnames are normalized to punycode before wildcard comparison
`https://&#x2764;.example/`|`https://xn--qei.example/`|No   |Non-ASCII hostnames are normalized to punycode before wildcard comparison

```cpp
    wil::com_ptr<ICoreWebView2_22> webView = m_webView.try_query<ICoreWebView2_22>();
    if (webView)
    {
        // Filter must be added for application to receive any WebResourceRequested event
        CHECK_FAILURE(webView->AddWebResourceRequestedFilterWithRequestSourceKinds(
            L"*worker.js", COREWEBVIEW2_WEB_RESOURCE_CONTEXT_ALL,
            COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_ALL));
        CHECK_FAILURE(m_webView->add_WebResourceRequested(
            Callback<ICoreWebView2WebResourceRequestedEventHandler>(
                [this](ICoreWebView2* sender, ICoreWebView2WebResourceRequestedEventArgs* args)
                {
                    wil::com_ptr<ICoreWebView2WebResourceRequestedEventArgs2>
                        webResourceRequestArgs;
                    if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&webResourceRequestArgs))))
                    {
                        COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS requestSourceKind =
                            COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_ALL;
                        CHECK_FAILURE(webResourceRequestArgs->get_RequestedSourceKind(
                            &requestSourceKind));
                        // Ensure that script is from shared worker source
                        if (requestSourceKind ==
                            COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS_SHARED_WORKER)
                        {
                            Microsoft::WRL::ComPtr<IStream> response_stream;
                            CHECK_FAILURE(SHCreateStreamOnFileEx(
                                L"assets/DemoWorker.js", STGM_READ, FILE_ATTRIBUTE_NORMAL,
                                FALSE, nullptr, &response_stream));

                            Microsoft::WRL::ComPtr<ICoreWebView2WebResourceResponse> response;
                            // Get the default webview environment
                            Microsoft::WRL::ComPtr<ICoreWebView2_2> webview2;
                            CHECK_FAILURE(sender->QueryInterface(IID_PPV_ARGS(&webview2)));

                            Microsoft::WRL::ComPtr<ICoreWebView2Environment> environment;
                            CHECK_FAILURE(webview2->get_Environment(&environment));
                            CHECK_FAILURE(environment->CreateWebResourceResponse(
                                response_stream.Get(), 200, L"OK", L"", &response));

                            CHECK_FAILURE(args->put_Response(response.Get()));
                        }
                    }
                    return S_OK;
                })
                .Get(),
            &m_webResourceRequestedToken));
    }
```

#### RemoveWebResourceRequestedFilterWithRequestSourceKinds

Removes a matching WebResource filter that was previously added for the `WebResourceRequested` event.

> public HRESULT [RemoveWebResourceRequestedFilterWithRequestSourceKinds](#removewebresourcerequestedfilterwithrequestsourcekinds)(LPCWSTR const uri, COREWEBVIEW2_WEB_RESOURCE_CONTEXT const resourceContext, COREWEBVIEW2_WEB_RESOURCE_REQUEST_SOURCE_KINDS const requestSourceKinds)

If the same filter was added multiple times, then it must be removed as many times as it was added for the removal to be effective. Returns `E_INVALIDARG` for a filter that was not added or is already removed. If the filter was added for multiple requestSourceKinds and removed just for one of them the filter remains for the non-removed requestSourceKinds.

