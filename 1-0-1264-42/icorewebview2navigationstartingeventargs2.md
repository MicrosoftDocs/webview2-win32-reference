---
description: The AdditionalAllowedFrameAncestors API that enable developers to provide additional allowed frame ancestors.
title: WebView2 Win32 C++ ICoreWebView2NavigationStartingEventArgs2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2NavigationStartingEventArgs2
---

# interface ICoreWebView2NavigationStartingEventArgs2

```
interface ICoreWebView2NavigationStartingEventArgs2
  : public ICoreWebView2NavigationStartingEventArgs
```

The AdditionalAllowedFrameAncestors API that enable developers to provide additional allowed frame ancestors.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[get_AdditionalAllowedFrameAncestors](#get_additionalallowedframeancestors) | Get additional allowed frame ancestors set by the host app.
[put_AdditionalAllowedFrameAncestors](#put_additionalallowedframeancestors) | The app may set this property to allow a frame to be embedded by additional ancestors besides what is allowed by http header [X-Frame-Options](https://developer.mozilla.org/docs/Web/HTTP/Headers/X-Frame-Options) and [Content-Security-Policy frame-ancestors directive](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors).

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1108.44
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### get_AdditionalAllowedFrameAncestors

Get additional allowed frame ancestors set by the host app.

> public HRESULT [get_AdditionalAllowedFrameAncestors](#get_additionalallowedframeancestors)(LPWSTR * value)

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### put_AdditionalAllowedFrameAncestors

The app may set this property to allow a frame to be embedded by additional ancestors besides what is allowed by http header [X-Frame-Options](https://developer.mozilla.org/docs/Web/HTTP/Headers/X-Frame-Options) and [Content-Security-Policy frame-ancestors directive](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors).

> public HRESULT [put_AdditionalAllowedFrameAncestors](#put_additionalallowedframeancestors)(LPCWSTR value)

If set, a frame ancestor is allowed if it is allowed by the additional allowed frame ancestors or original http header from the site. Whether an ancestor is allowed by the additional allowed frame ancestors is done the same way as if the site provided it as the source list of the Content-Security-Policy frame-ancestors directive. For example, if `https://example.com` and `https://www.example.com` are the origins of the top page and intermediate iframes that embed a nested site-embedding iframe, and you fully trust those origins, you should set this property to `https://example.comhttps://www.example.com`. This property gives the app the ability to use iframe to embed sites that otherwise could not be embedded in an iframe in trusted app pages. This could potentially subject the embedded sites to [Clickjacking](https://en.wikipedia.org/wiki/Clickjacking) attack from the code running in the embedding web page. Therefore, you should only set this property with origins of fully trusted embedding page and any intermediate iframes. Whenever possible, you should use the list of specific origins of the top and intermediate frames instead of wildcard characters for this property. This API is to provide limited support for app scenarios that used to be supported by `<webview>` element in other solutions like JavaScript UWP apps and Electron. You should limit the usage of this property to trusted pages, and specific navigation target url, by checking the `Source` of the WebView2, and `Uri` of the event args.

This property is ignored for top level document navigation.

```cpp
const std::wstring myTrustedSite = L"https://appassets.example";
const std::wstring siteToEmbed = L"https://www.microsoft.com";

// The trusted page is using <iframe name="my_site_embedding_frame">
// element to embed other sites.
const std::wstring siteEmbeddingFrameName = L"my_site_embedding_frame";

bool AreSitesSame(PCWSTR url1, PCWSTR url2)
{
    wil::com_ptr<IUri> uri1;
    CHECK_FAILURE(CreateUri(url1, Uri_CREATE_CANONICALIZE, 0, &uri1));
    DWORD scheme1 = -1;
    DWORD port1 = 0;
    wil::unique_bstr host1;
    CHECK_FAILURE(uri1->GetScheme(&scheme1));
    CHECK_FAILURE(uri1->GetHost(&host1));
    CHECK_FAILURE(uri1->GetPort(&port1));
    wil::com_ptr<IUri> uri2;
    CHECK_FAILURE(CreateUri(url2, Uri_CREATE_CANONICALIZE, 0, &uri2));
    DWORD scheme2 = -1;
    DWORD port2 = 0;
    wil::unique_bstr host2;
    CHECK_FAILURE(uri2->GetScheme(&scheme2));
    CHECK_FAILURE(uri2->GetHost(&host2));
    CHECK_FAILURE(uri2->GetPort(&port2));
    return (scheme1 == scheme2) && (port1 == port2) && (wcscmp(host1.get(), host2.get()) == 0);
}

// App specific logic to decide whether the page is fully trusted.
bool IsAppContentUri(PCWSTR pageUrl)
{
    return AreSitesSame(pageUrl, myTrustedSite.c_str());
}

// App specific logic to decide whether a site is the one it wants to embed.
bool IsTargetSite(PCWSTR siteUrl)
{
    return AreSitesSame(siteUrl, siteToEmbed.c_str());
}
```

```cpp
        // Set up the event listeners to handle site embedding scenario. The code will take effect
        // when the site embedding page is navigated to and the embedding iframe navigates to the
        // site that we want to embed.

        // This part is trying to scope the API usage to the specific scenario where we are
        // embedding a site. The result is recorded in m_siteEmbeddingIFrameCount.
        CHECK_FAILURE(webview2_4->add_FrameCreated(
            Callback<ICoreWebView2FrameCreatedEventHandler>(
                [this](ICoreWebView2* sender, ICoreWebView2FrameCreatedEventArgs* args)
                    -> HRESULT 
                {
                    wil::com_ptr<ICoreWebView2Frame> webviewFrame;
                    CHECK_FAILURE(args->get_Frame(&webviewFrame));
                    wil::unique_cotaskmem_string page_url;
                    CHECK_FAILURE(m_webView->get_Source(&page_url));
                    // IsAppContentUri verifies that page_url belongs to  the app.
                    if (IsAppContentUri(page_url.get()))
                    {
                        // We are on trusted pages. Now check whether it is the iframe we plan
                        // to embed arbitrary sites.
                        wil::unique_cotaskmem_string frame_name;
                        CHECK_FAILURE(webviewFrame->get_Name(&frame_name));
                        if (siteEmbeddingFrameName == frame_name.get())
                        {
                            ++m_siteEmbeddingIFrameCount;
                            CHECK_FAILURE(webviewFrame->add_Destroyed(
                                Microsoft::WRL::Callback<
                                    ICoreWebView2FrameDestroyedEventHandler>(
                                    [this](
                                        ICoreWebView2Frame* sender, IUnknown* args) -> HRESULT
                                    {
                                        --m_siteEmbeddingIFrameCount;
                                        return S_OK;
                                    })
                                    .Get(),
                                nullptr));
                        }
                    }
                    return S_OK;
                })
                .Get(),
            nullptr));

        // Using FrameNavigationStarting event instead of NavigationStarting event of
        // CoreWebViewFrame to cover all possible nested iframes inside the embedded site as
        // CoreWebViewFrame object currently only support first level iframes in the top page.
        CHECK_FAILURE(m_webView->add_FrameNavigationStarting(
            Microsoft::WRL::Callback<ICoreWebView2NavigationStartingEventHandler>(
                [this](ICoreWebView2* sender, ICoreWebView2NavigationStartingEventArgs* args)
                    -> HRESULT
                {
                    if (m_siteEmbeddingIFrameCount > 0)
                    {
                        wil::unique_cotaskmem_string navigationTargetUri;
                        CHECK_FAILURE(args->get_Uri(&navigationTargetUri));
                        if (IsTargetSite(navigationTargetUri.get()))
                        {
                            wil::com_ptr<ICoreWebView2NavigationStartingEventArgs2>
                                navigationStartArgs;
                            if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&navigationStartArgs))))
                            {
                                navigationStartArgs->put_AdditionalAllowedFrameAncestors(
                                    myTrustedSite.c_str());
                            }
                        }
                    }
                    return S_OK;
                })
                .Get(),
            nullptr));
```

