---
description: This interface is an extension of ICoreWebView2_9 that supports BasicAuthenticationRequested event.
title: WebView2 Win32 C++ ICoreWebView2_10
ms.date: 06/26/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_10
topic_type: 
- APIRef
api_name:
- ICoreWebView2_10
- ICoreWebView2_10.add_BasicAuthenticationRequested
- ICoreWebView2_10.remove_BasicAuthenticationRequested
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_10

```
interface ICoreWebView2_10
  : public ICoreWebView2_9
```

This interface is an extension of [ICoreWebView2_9](icorewebview2_9.md#icorewebview2_9) that supports BasicAuthenticationRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BasicAuthenticationRequested](#add_basicauthenticationrequested) | Adds an event handler for the `BasicAuthenticationRequested` event.
[remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested) | Removes an event handler previously added with `add_BasicAuthenticationRequested`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_BasicAuthenticationRequested

Adds an event handler for the `BasicAuthenticationRequested` event.

> public HRESULT [add_BasicAuthenticationRequested](#add_basicauthenticationrequested)([ICoreWebView2BasicAuthenticationRequestedEventHandler](icorewebview2basicauthenticationrequestedeventhandler.md#icorewebview2basicauthenticationrequestedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the BasicAuthenticationRequested event. BasicAuthenticationRequested event is raised when WebView encounters a Basic HTTP Authentication request as described in https://developer.mozilla.org/docs/Web/HTTP/Authentication, a Digest HTTP Authentication request as described in https://developer.mozilla.org/docs/Web/HTTP/Headers/Authorization#digest, an NTLM authentication or a Proxy Authentication request.

The host can provide a response with credentials for the authentication or cancel the request. If the host sets the Cancel property to false but does not provide either UserName or Password properties on the Response property, then WebView2 will show the default authentication challenge dialog prompt to the user.

```cpp
    if (auto webView10 = m_webView.try_query<ICoreWebView2_10>())
    {
        CHECK_FAILURE(webView10->add_BasicAuthenticationRequested(
            Callback<ICoreWebView2BasicAuthenticationRequestedEventHandler>(
                [this](
                    ICoreWebView2* sender,
                    ICoreWebView2BasicAuthenticationRequestedEventArgs* args) {
                    wil::com_ptr<ICoreWebView2BasicAuthenticationResponse> basicAuthenticationResponse;
                    CHECK_FAILURE(args->get_Response(&basicAuthenticationResponse));
                    CHECK_FAILURE(basicAuthenticationResponse->put_UserName(L"user"));
                    CHECK_FAILURE(basicAuthenticationResponse->put_Password(L"pass"));

                    return S_OK;
                })
                .Get(),
            &m_basicAuthenticationRequestedToken));
    }
    else {
        FeatureNotAvailable();
    }
```

#### remove_BasicAuthenticationRequested

Removes an event handler previously added with `add_BasicAuthenticationRequested`.

> public HRESULT [remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested)(EventRegistrationToken token)

