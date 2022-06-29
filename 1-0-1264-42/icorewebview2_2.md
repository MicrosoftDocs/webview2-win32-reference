---
description: A continuation of the ICoreWebView2 interface.
title: WebView2 Win32 C++ ICoreWebView2_2
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_2
---

# interface ICoreWebView2_2

```
interface ICoreWebView2_2
  : public ICoreWebView2
```

A continuation of the [ICoreWebView2](icorewebview2.md) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DOMContentLoaded](#add_domcontentloaded) | Add an event handler for the DOMContentLoaded event.
[add_WebResourceResponseReceived](#add_webresourceresponsereceived) | Add an event handler for the WebResourceResponseReceived event.
[get_CookieManager](#get_cookiemanager) | Gets the cookie manager object associated with this [ICoreWebView2](icorewebview2.md).
[get_Environment](#get_environment) | Exposes the CoreWebView2Environment used to create this CoreWebView2.
[NavigateWithWebResourceRequest](#navigatewithwebresourcerequest) | Navigates using a constructed WebResourceRequest object.
[remove_DOMContentLoaded](#remove_domcontentloaded) | Remove an event handler previously added with add_DOMContentLoaded.
[remove_WebResourceResponseReceived](#remove_webresourceresponsereceived) | Remove an event handler previously added with add_WebResourceResponseReceived.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.705.50
WebView2 Win32 Prerelease |    1.0.721

## Members

#### add_DOMContentLoaded

Add an event handler for the DOMContentLoaded event.

> public HRESULT [add_DOMContentLoaded](#add_domcontentloaded)([ICoreWebView2DOMContentLoadedEventHandler](icorewebview2domcontentloadedeventhandler.md) * eventHandler, EventRegistrationToken * token)

DOMContentLoaded is raised when the initial html document has been parsed. This aligns with the document's DOMContentLoaded event in html.

```cpp
    // Register a handler for the DOMContentLoaded event.
    // Check whether the DOM content loaded
    CHECK_FAILURE(m_appWindow->GetWebView()->QueryInterface(IID_PPV_ARGS(&m_webView2)));
    CHECK_FAILURE(m_webView2->add_DOMContentLoaded(
        Callback<ICoreWebView2DOMContentLoadedEventHandler>(
            [this](ICoreWebView2* sender, ICoreWebView2DOMContentLoadedEventArgs* args)
                -> HRESULT {
                m_webView->ExecuteScript(
                    LR"~(
                    let content = document.createElement("h2");
                    content.style.color = 'blue';
                    content.textContent = "This text was added by the host app";
                    document.body.appendChild(content);
                    )~",
                    Callback<ICoreWebView2ExecuteScriptCompletedHandler>(
                        [](HRESULT error, PCWSTR result) -> HRESULT { return S_OK; })
                        .Get());
                return S_OK;
            })
            .Get(),
        &m_DOMContentLoadedToken));
```

#### add_WebResourceResponseReceived

Add an event handler for the WebResourceResponseReceived event.

> public HRESULT [add_WebResourceResponseReceived](#add_webresourceresponsereceived)([ICoreWebView2WebResourceResponseReceivedEventHandler](icorewebview2webresourceresponsereceivedeventhandler.md) * eventHandler, EventRegistrationToken * token)

WebResourceResponseReceived is raised when the WebView receives the response for a request for a web resource (any URI resolution performed by the WebView; such as HTTP/HTTPS, file and data requests from redirects, navigations, declarations in HTML, implicit favicon lookups, and fetch API usage in the document). The host app can use this event to view the actual request and response for a web resource. There is no guarantee about the order in which the WebView processes the response and the host app's handler runs. The app's handler will not block the WebView from processing the response. 
```cpp
    CHECK_FAILURE(m_webView->add_WebResourceResponseReceived(
        Callback<ICoreWebView2WebResourceResponseReceivedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2WebResourceResponseReceivedEventArgs* args) {
                wil::com_ptr<ICoreWebView2WebResourceRequest> request;
                CHECK_FAILURE(args->get_Request(&request));
                wil::unique_cotaskmem_string uri;
                CHECK_FAILURE(request->get_Uri(&uri));
                if (wcscmp(uri.get(), L"https://authenticationtest.com/HTTPAuth/") == 0)
                {
                    wil::com_ptr<ICoreWebView2HttpRequestHeaders> requestHeaders;
                    CHECK_FAILURE(request->get_Headers(&requestHeaders));

                    wil::unique_cotaskmem_string authHeaderValue;
                    if (requestHeaders->GetHeader(L"Authorization", &authHeaderValue) == S_OK)
                    {
                        m_appWindow->AsyncMessageBox(
                            std::wstring(L"Authorization: ") + authHeaderValue.get(),
                            L"Authentication result");
                        m_appWindow->DeleteComponent(this);
                    }
                }

                return S_OK;
            })
            .Get(),
        &m_webResourceResponseReceivedToken));
```

#### get_CookieManager

Gets the cookie manager object associated with this [ICoreWebView2](icorewebview2.md).

> public HRESULT [get_CookieManager](#get_cookiemanager)([ICoreWebView2CookieManager](icorewebview2cookiemanager.md) ** cookieManager)

See [ICoreWebView2CookieManager](icorewebview2cookiemanager.md).

```cpp
    auto webview2_2 = m_webView.try_query<ICoreWebView2_2>();
    CHECK_FEATURE_RETURN_EMPTY(webview2_2);
    CHECK_FAILURE(webview2_2->get_CookieManager(&m_cookieManager));
```

#### get_Environment

Exposes the CoreWebView2Environment used to create this CoreWebView2.

> public HRESULT [get_Environment](#get_environment)([ICoreWebView2Environment](icorewebview2environment.md) ** environment)

#### NavigateWithWebResourceRequest

Navigates using a constructed WebResourceRequest object.

> public HRESULT [NavigateWithWebResourceRequest](#navigatewithwebresourcerequest)([ICoreWebView2WebResourceRequest](icorewebview2webresourcerequest.md) * request)

This lets you provide post data or additional request headers during navigation. The headers in the WebResourceRequest override headers added by WebView2 runtime except for Cookie headers. Method can only be either "GET" or "POST". Provided post data will only be sent only if the method is "POST" and the uri scheme is HTTP(S). 
```cpp
        wil::com_ptr<ICoreWebView2Environment2> webviewEnvironment2;
        CHECK_FAILURE(appWindow->GetWebViewEnvironment()->QueryInterface(
            IID_PPV_ARGS(&webviewEnvironment2)));
        wil::com_ptr<ICoreWebView2WebResourceRequest> webResourceRequest;
        wil::com_ptr<IStream> postDataStream = SHCreateMemStream(
            reinterpret_cast<const BYTE*>(postDataBytes.get()), sizeNeededForMultiByte);

        // This is acts as a form submit to https://www.w3schools.com/action_page.php
        CHECK_FAILURE(webviewEnvironment2->CreateWebResourceRequest(
            L"https://www.w3schools.com/action_page.php", L"POST", postDataStream.get(),
            L"Content-Type: application/x-www-form-urlencoded", &webResourceRequest));
        wil::com_ptr<ICoreWebView2_2> webview2;
        CHECK_FAILURE(m_appWindow->GetWebView()->QueryInterface(IID_PPV_ARGS(&webview2)));
        CHECK_FAILURE(webview2->NavigateWithWebResourceRequest(webResourceRequest.get()));
```

#### remove_DOMContentLoaded

Remove an event handler previously added with add_DOMContentLoaded.

> public HRESULT [remove_DOMContentLoaded](#remove_domcontentloaded)(EventRegistrationToken token)

#### remove_WebResourceResponseReceived

Remove an event handler previously added with add_WebResourceResponseReceived.

> public HRESULT [remove_WebResourceResponseReceived](#remove_webresourceresponsereceived)(EventRegistrationToken token)

