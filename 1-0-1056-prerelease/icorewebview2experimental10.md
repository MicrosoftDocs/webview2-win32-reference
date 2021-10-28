---
description: 
title: WebView2 Win32 C++ ICoreWebView2Experimental10
ms.date: 10/28/2021
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental10
---

# interface ICoreWebView2Experimental10

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental10
  : public IUnknown
```

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_BasicAuthenticationRequested](#add_basicauthenticationrequested) | Add an event handler for the BasicAuthenticationRequested event.
[remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested) | Remove an event handler previously added with add_WebResourceRequested.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.1056

## Members

#### add_BasicAuthenticationRequested

Add an event handler for the BasicAuthenticationRequested event.

> public HRESULT [add_BasicAuthenticationRequested](#add_basicauthenticationrequested)([ICoreWebView2ExperimentalBasicAuthenticationRequestedEventHandler](icorewebview2experimentalbasicauthenticationrequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

BasicAuthenticationRequested event is raised when WebView encounters a Basic HTTP Authentication request as described in https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication or an NTLM authentication request.

The host can provide a response with credentials for the authentication or cancel the request. If the host doesn't set the Cancel property to true or set either UserName or Password properties on the Response property, then WebView2 will show the default authentication challenge dialog prompt to the user.

```cpp
    if (auto webViewExperimental10 = m_webView.try_query<ICoreWebView2Experimental10>())
    {
        CHECK_FAILURE(webViewExperimental10->add_BasicAuthenticationRequested(
            Callback<ICoreWebView2ExperimentalBasicAuthenticationRequestedEventHandler>(
                [this](
                    ICoreWebView2* sender,
                    ICoreWebView2ExperimentalBasicAuthenticationRequestedEventArgs* args) {
                    wil::com_ptr<ICoreWebView2ExperimentalBasicAuthenticationResponse> basicAuthenticationResponse;
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

Remove an event handler previously added with add_WebResourceRequested.

> public HRESULT [remove_BasicAuthenticationRequested](#remove_basicauthenticationrequested)(EventRegistrationToken token)

