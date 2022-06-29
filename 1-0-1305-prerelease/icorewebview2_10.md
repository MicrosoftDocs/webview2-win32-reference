---
description: This interface is an extension of ICoreWebView2_9 that supports BasicAuthenticationRequested event.
title: WebView2 Win32 C++ ICoreWebView2_10
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_10
---

# interface ICoreWebView2_10

```
interface ICoreWebView2_10
  : public ICoreWebView2_9
```

This interface is an extension of [ICoreWebView2_9](icorewebview2_9.md) that supports BasicAuthenticationRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BasicAuthenticationRequested](#add_basicauthenticationrequested) | Add an event handler for the BasicAuthenticationRequested event.
[remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested) | Remove an event handler previously added with add_BasicAuthenticationRequested.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1150.38
WebView2 Win32 Prerelease |    1.0.1133

## Members

#### add_BasicAuthenticationRequested

Add an event handler for the BasicAuthenticationRequested event.

> public HRESULT [add_BasicAuthenticationRequested](#add_basicauthenticationrequested)([ICoreWebView2BasicAuthenticationRequestedEventHandler](icorewebview2basicauthenticationrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

BasicAuthenticationRequested event is raised when WebView encounters a Basic HTTP Authentication request as described in https://developer.mozilla.org/docs/Web/HTTP/Authentication, an NTLM authentication or a Proxy Authentication request.

The host can provide a response with credentials for the authentication or cancel the request. If the host doesn't set the Cancel property to true or set either UserName or Password properties on the Response property, then WebView2 will show the default authentication challenge dialog prompt to the user.

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

Remove an event handler previously added with add_BasicAuthenticationRequested.

> public HRESULT [remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested)(EventRegistrationToken token)

