---
description: This interface is an extension of ICoreWebView2_13 that adds ServerCertificate support.
title: WebView2 Win32 C++ ICoreWebView2_14
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_14
---

# interface ICoreWebView2_14

```
interface ICoreWebView2_14
  : public ICoreWebView2_13
```

This interface is an extension of [ICoreWebView2_13](icorewebview2_13.md) that adds ServerCertificate support.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ServerCertificateErrorDetected](#add_servercertificateerrordetected) | Add an event handler for the ServerCertificateErrorDetected event.
[ClearServerCertificateErrorActions](#clearservercertificateerroractions) | Clears all cached decisions to proceed with TLS certificate errors from the ServerCertificateErrorDetected event for all WebView2's sharing the same session.
[remove_ServerCertificateErrorDetected](#remove_servercertificateerrordetected) | Remove an event handler previously added with add_ServerCertificateErrorDetected.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### add_ServerCertificateErrorDetected

Add an event handler for the ServerCertificateErrorDetected event.

> public HRESULT [add_ServerCertificateErrorDetected](#add_servercertificateerrordetected)([ICoreWebView2ServerCertificateErrorDetectedEventHandler](icorewebview2servercertificateerrordetectedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The ServerCertificateErrorDetected event is raised when the WebView2 cannot verify server's digital certificate while loading a web page.

This event will raise for all web resources and follows the `WebResourceRequested` event.

If you don't handle the event, WebView2 will show the default TLS interstitial error page to the user for navigations, and for non-navigations the web request is cancelled.

WebView2 caches the response when action is `COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_ALWAYS_ALLOW` for the RequestUri's host and the server certificate in the session and the `ServerCertificateErrorDetected` event won't be raised again.

To raise the event again you must clear the cache using `ClearServerCertificateErrorActions`.

```cpp
// When WebView2 doesn't trust a TLS certificate but host app does, this example bypasses
// the default TLS interstitial page using the ServerCertificateErrorDetected event handler and
// continues the request to a server. Otherwise, cancel the request.
void SettingsComponent::ToggleCustomServerCertificateSupport()
{
    if (m_webView2_14)
    {
        if (m_ServerCertificateErrorToken.value == 0)
        {
            CHECK_FAILURE(m_webView2_14->add_ServerCertificateErrorDetected(
                Callback<ICoreWebView2ServerCertificateErrorDetectedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2ServerCertificateErrorDetectedEventArgs* args) {
                        COREWEBVIEW2_WEB_ERROR_STATUS errorStatus;
                        CHECK_FAILURE(args->get_ErrorStatus(&errorStatus));

                        wil::com_ptr<ICoreWebView2Certificate> certificate = nullptr;
                        CHECK_FAILURE(args->get_ServerCertificate(&certificate));

                        // Continues the request to a server with a TLS certificate if the error
                        // status is of type
                        // `COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_IS_INVALID` and trusted by
                        // the host app.
                        if (errorStatus ==
                                COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_IS_INVALID &&
                            ValidateServerCertificate(certificate.get()))
                        {
                            CHECK_FAILURE(args->put_Action(
                                COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_ALWAYS_ALLOW));
                        }
                        else
                        {
                            // Cancel the request for other TLS certificate error types or if
                            // untrusted by the host app.
                            CHECK_FAILURE(args->put_Action(
                                COREWEBVIEW2_SERVER_CERTIFICATE_ERROR_ACTION_CANCEL));
                        }
                        return S_OK;
                    })
                    .Get(),
                &m_ServerCertificateErrorToken));
        }
        else
        {
            CHECK_FAILURE(m_webView2_14->remove_ServerCertificateErrorDetected(
                m_ServerCertificateErrorToken));
            m_ServerCertificateErrorToken.value = 0;
        }
    }
    else
    {
        FeatureNotAvailable();
    }
}
```

#### ClearServerCertificateErrorActions

Clears all cached decisions to proceed with TLS certificate errors from the ServerCertificateErrorDetected event for all WebView2's sharing the same session.

> public HRESULT [ClearServerCertificateErrorActions](#clearservercertificateerroractions)([ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler](icorewebview2clearservercertificateerroractionscompletedhandler.md) * handler)

#### remove_ServerCertificateErrorDetected

Remove an event handler previously added with add_ServerCertificateErrorDetected.

> public HRESULT [remove_ServerCertificateErrorDetected](#remove_servercertificateerrordetected)(EventRegistrationToken token)

