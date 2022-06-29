---
description: A continuation of the ICoreWebView2_4 interface to support ClientCertificateRequested event.
title: WebView2 Win32 C++ ICoreWebView2_5
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2_5
---

# interface ICoreWebView2_5

```
interface ICoreWebView2_5
  : public ICoreWebView2_4
```

A continuation of the [ICoreWebView2_4](icorewebview2_4.md) interface to support ClientCertificateRequested event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ClientCertificateRequested](#add_clientcertificaterequested) | Add an event handler for the ClientCertificateRequested event.
[remove_ClientCertificateRequested](#remove_clientcertificaterequested) | Remove an event handler previously added with add_ClientCertificateRequested.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    1.0.961.33
WebView2 Win32 Prerelease |    1.0.955

## Members

#### add_ClientCertificateRequested

Add an event handler for the ClientCertificateRequested event.

> public HRESULT [add_ClientCertificateRequested](#add_clientcertificaterequested)([ICoreWebView2ClientCertificateRequestedEventHandler](icorewebview2clientcertificaterequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The ClientCertificateRequested event is raised when the WebView2 is making a request to an HTTP server that needs a client certificate for HTTP authentication. Read more about HTTP client certificates at [RFC 8446 The Transport Layer Security (TLS) Protocol Version 1.3](https://tools.ietf.org/html/rfc8446).

With this event you have several options for responding to client certificate requests:

Scenario   |Handled   |Cancel   |SelectedCertificate
--------- | --------- | --------- | ---------
Respond to server with a certificate   |True   |False   |MutuallyTrustedCertificate value
Respond to server without certificate   |True   |False   |null
Display default client certificate selection dialog prompt   |False   |False   |n/a
Cancel the request   |n/a   |True   |n/a

If you don't handle the event, WebView2 will show the default client certificate selection dialog prompt to user.

```cpp
void SettingsComponent::EnableCustomClientCertificateSelection()
{
    if (m_webView2_5)
    {
        if (m_ClientCertificateRequestedToken.value == 0)
        {
            CHECK_FAILURE(m_webView2_5->add_ClientCertificateRequested(
                Callback<ICoreWebView2ClientCertificateRequestedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2ClientCertificateRequestedEventArgs* args) {
                        wil::com_ptr<ICoreWebView2ClientCertificateCollection>
                            certificateCollection;
                        CHECK_FAILURE(
                            args->get_MutuallyTrustedCertificates(&certificateCollection));

                        UINT certificateCollectionCount = 0;
                        CHECK_FAILURE(
                            certificateCollection->get_Count(&certificateCollectionCount));
                        wil::com_ptr<ICoreWebView2ClientCertificate> certificate = nullptr;

                        if (certificateCollectionCount > 0)
                        {
                            // There is no significance to the order, picking a certificate
                            // arbitrarily.
                            CHECK_FAILURE(certificateCollection->GetValueAtIndex(
                                certificateCollectionCount - 1, &certificate));
                            // Continue with the selected certificate to respond to the server.
                            CHECK_FAILURE(args->put_SelectedCertificate(certificate.get()));
                            CHECK_FAILURE(args->put_Handled(TRUE));
                        }
                        else
                        {
                            // Continue without a certificate to respond to the server if
                            // certificate collection is empty.
                            CHECK_FAILURE(args->put_Handled(TRUE));
                        }
                        return S_OK;
                    })
                    .Get(),
                &m_ClientCertificateRequestedToken));
        }
        else
        {
            CHECK_FAILURE(m_webView2_5->remove_ClientCertificateRequested(
                m_ClientCertificateRequestedToken));
            m_ClientCertificateRequestedToken.value = 0;
        }
    }
}
```

```cpp
    m_webView2_5 = m_webView.try_query<ICoreWebView2_5>();
    if (m_webView2_5)
    {
        CHECK_FAILURE(
            m_webView2_5->add_ClientCertificateRequested(
                Callback<ICoreWebView2ClientCertificateRequestedEventHandler>(
                    [this](
                        ICoreWebView2* sender,
                        ICoreWebView2ClientCertificateRequestedEventArgs* args) {
                        auto showDialog = [this, args] {
                            wil::com_ptr<ICoreWebView2ClientCertificateCollection>
                                certificateCollection;
                            CHECK_FAILURE(args->get_MutuallyTrustedCertificates(&certificateCollection));

                            wil::unique_cotaskmem_string host;
                            CHECK_FAILURE(args->get_Host(&host));

                            INT port = FALSE;
                            CHECK_FAILURE(args->get_Port(&port));

                            UINT certificateCollectionCount;
                            CHECK_FAILURE(certificateCollection->get_Count(&certificateCollectionCount));

                            wil::com_ptr<ICoreWebView2ClientCertificate> certificate = nullptr;

                            if (certificateCollectionCount > 0)
                            {
                                ClientCertificate clientCertificate;
                                for (UINT i = 0; i < certificateCollectionCount; i++)
                                {
                                    CHECK_FAILURE(
                                        certificateCollection->GetValueAtIndex(i, &certificate));

                                    CHECK_FAILURE(certificate->get_Subject(&clientCertificate.Subject));

                                    CHECK_FAILURE(certificate->get_DisplayName(&clientCertificate.DisplayName));

                                    CHECK_FAILURE(certificate->get_Issuer(&clientCertificate.Issuer));

                                    COREWEBVIEW2_CLIENT_CERTIFICATE_KIND Kind;
                                    CHECK_FAILURE(
                                        certificate->get_Kind(&Kind));
                                    clientCertificate.CertificateKind = NameOfCertificateKind(Kind);

                                    CHECK_FAILURE(certificate->get_ValidFrom(&clientCertificate.ValidFrom));

                                    CHECK_FAILURE(certificate->get_ValidTo(&clientCertificate.ValidTo));

                                    clientCertificates_.push_back(clientCertificate);
                                }

                                // Display custom dialog box for the client certificate selection.
                                ClientCertificateSelectionDialog dialog(
                                    m_appWindow->GetMainWindow(), L"Select a Certificate for authentication", host.get(), port, clientCertificates_);

                                if (dialog.confirmed)
                                {
                                    int selectedIndex = dialog.selectedItem;
                                    if (selectedIndex >= 0)
                                    {
                                        CHECK_FAILURE(
                                            certificateCollection->GetValueAtIndex(selectedIndex, &certificate));
                                        // Continue with the selected certificate to respond to the server if `OK` is selected.
                                        CHECK_FAILURE(args->put_SelectedCertificate(certificate.get()));
                                    }
                                }
                                // Continue without a certificate to respond to the server if `CANCEL` is selected.
                                CHECK_FAILURE(args->put_Handled(TRUE));
                            }
                            else
                            {
                                // Continue without a certificate to respond to the server if certificate collection is empty.
                                CHECK_FAILURE(args->put_Handled(TRUE));
                            }
                        };

                        // Obtain a deferral for the event so that the CoreWebView2
                        // doesn't examine the properties we set on the event args and
                        // after we call the Complete method asynchronously later.
                        wil::com_ptr<ICoreWebView2Deferral> deferral;
                        CHECK_FAILURE(args->GetDeferral(&deferral));

                        // complete the deferral asynchronously.
                        m_appWindow->RunAsync([deferral, showDialog]() {
                            showDialog();
                            CHECK_FAILURE(deferral->Complete());
                            });

                        return S_OK;
                    })
                    .Get(),
                &m_ClientCertificateRequestedToken));

        MessageBox(
            nullptr, L"Custom Client Certificate selection dialog will be used next when WebView2 "
            L"is making a request to an HTTP server that needs a client certificate.",
            L"Client certificate selection", MB_OK);
    }
    else
    {
        FeatureNotAvailable();
    }
```

#### remove_ClientCertificateRequested

Remove an event handler previously added with add_ClientCertificateRequested.

> public HRESULT [remove_ClientCertificateRequested](#remove_clientcertificaterequested)(EventRegistrationToken token)

