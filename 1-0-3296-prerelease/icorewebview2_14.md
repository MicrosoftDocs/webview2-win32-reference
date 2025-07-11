---
description: This interface is an extension of ICoreWebView2_13 that adds ServerCertificate support.
title: WebView2 Win32 C++ ICoreWebView2_14
ms.date: 05/06/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_14
topic_type: 
- APIRef
api_name:
- ICoreWebView2_14
- ICoreWebView2_14.add_ServerCertificateErrorDetected
- ICoreWebView2_14.ClearServerCertificateErrorActions
- ICoreWebView2_14.remove_ServerCertificateErrorDetected
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2_14

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

```
interface ICoreWebView2_14
  : public ICoreWebView2_13
```

This interface is an extension of [ICoreWebView2_13](icorewebview2_13.md#icorewebview2_13) that adds ServerCertificate support.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ServerCertificateErrorDetected](#add_servercertificateerrordetected) | Adds an event handler for the `ServerCertificateErrorDetected` event.
[ClearServerCertificateErrorActions](#clearservercertificateerroractions) | Clears all cached decisions to proceed with TLS certificate errors from the ServerCertificateErrorDetected event for all WebView2's sharing the same session.
[remove_ServerCertificateErrorDetected](#remove_servercertificateerrordetected) | Removes an event handler previously added with `add_ServerCertificateErrorDetected`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.1245.22
WebView2 Win32 Prerelease |    1.0.1248

## Members

#### add_ServerCertificateErrorDetected

Adds an event handler for the `ServerCertificateErrorDetected` event.

> public HRESULT [add_ServerCertificateErrorDetected](#add_servercertificateerrordetected)([ICoreWebView2ServerCertificateErrorDetectedEventHandler](icorewebview2servercertificateerrordetectedeventhandler.md#icorewebview2servercertificateerrordetectedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the ServerCertificateErrorDetected event. The ServerCertificateErrorDetected event is raised when the WebView2 cannot verify server's digital certificate while loading a web page.

This event will raise for all web resources and follows the `WebResourceRequested` event.

If you don't handle the event, WebView2 will show the default TLS interstitial error page to the user for navigations, and for non-navigations the web request is cancelled.

Note that WebView2 before raising `ServerCertificateErrorDetected` raises a `NavigationCompleted` event with `IsSuccess` as FALSE and any of the below WebErrorStatuses that indicate a certificate failure.

* COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_COMMON_NAME_IS_INCORRECT

* COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_EXPIRED

* COREWEBVIEW2_WEB_ERROR_STATUS_CLIENT_CERTIFICATE_CONTAINS_ERRORS

* COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_REVOKED

* COREWEBVIEW2_WEB_ERROR_STATUS_CERTIFICATE_IS_INVALID

For more details see [ICoreWebView2NavigationCompletedEventArgs::get_IsSuccess](icorewebview2navigationcompletedeventargs.md#get_issuccess) and handle ServerCertificateErrorDetected event or show the default TLS interstitial error page to the user according to the app needs.

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
                        ICoreWebView2ServerCertificateErrorDetectedEventArgs* args)
                    {
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

> public HRESULT [ClearServerCertificateErrorActions](#clearservercertificateerroractions)([ICoreWebView2ClearServerCertificateErrorActionsCompletedHandler](icorewebview2clearservercertificateerroractionscompletedhandler.md#icorewebview2clearservercertificateerroractionscompletedhandler) * handler)

#### remove_ServerCertificateErrorDetected

Removes an event handler previously added with `add_ServerCertificateErrorDetected`.

> public HRESULT [remove_ServerCertificateErrorDetected](#remove_servercertificateerrordetected)(EventRegistrationToken token)

