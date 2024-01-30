---
description: The ICoreWebView2 Experimental interface to support client certificates.
title: WebView2 Win32 C++ ICoreWebView2Experimental3
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 07/26/2021
ms.topic: reference
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental3
---

# interface ICoreWebView2Experimental3

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental3
  : public IUnknown
```

The ICoreWebView2 Experimental interface to support client certificates.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ClientCertificateRequested](#add_clientcertificaterequested) | Add an event handler for the ClientCertificateRequested event.
[remove_ClientCertificateRequested](#remove_clientcertificaterequested) | Remove an event handler previously added with add_ClientCertificateRequested.
[COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind) | Specifies the browser process exit type used in the ICoreWebView2ExperimentalBrowserProcessExitedEventArgs interface.
[COREWEBVIEW2_CLIENT_CERTIFICATE_KIND](#corewebview2_client_certificate_kind) | Specifies the client certificate kind.
[COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4) | Matrix that represents a 3D transform.
[COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status) | Status of UpdateRuntime operation result.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.902

## Members

#### add_ClientCertificateRequested

Add an event handler for the ClientCertificateRequested event.

> public HRESULT [add_ClientCertificateRequested](#add_clientcertificaterequested)([ICoreWebView2ExperimentalClientCertificateRequestedEventHandler](icorewebview2experimentalclientcertificaterequestedeventhandler.md) * eventHandler, EventRegistrationToken * token)

The ClientCertificateRequested event is raised when the WebView2 is making a request to an HTTP server that needs a client certificate for HTTP authentication. Read more about HTTP client certificates at [RFC 8446 The Transport Layer Security (TLS) Protocol Version 1.3](https://tools.ietf.org/html/rfc8446).

With this event you have several options for responding to client certificate requests:

Scenario  |Handled  |Cancel  |SelectedCertificate
--------- | --------- | --------- | ---------
Respond to server with a certificate  |True  |False  |MutuallyTrustedCertificate value
Respond to server without certificate  |True  |False  |null
Display default client certificate selection dialog prompt  |False  |False  |n/a
Cancel the request  |n/a  |True  |n/a

If you don't handle the event, WebView2 will show the default client certificate selection dialog prompt to user.

```cpp
void SettingsComponent::EnableCustomClientCertificateSelection()
{
    if (m_ClientCertificateRequestedToken.value == 0)
    {
        CHECK_FAILURE(m_webViewExperimental->add_ClientCertificateRequested(
            Callback<ICoreWebView2ExperimentalClientCertificateRequestedEventHandler>(
                [this](
                    ICoreWebView2* sender,
                    ICoreWebView2ExperimentalClientCertificateRequestedEventArgs* args) {
                        wil::com_ptr<ICoreWebView2ExperimentalClientCertificateCollection> certificateCollection;
                        CHECK_FAILURE(args->get_MutuallyTrustedCertificates(&certificateCollection));

                        UINT certificateCollectionCount = 0;
                        CHECK_FAILURE(certificateCollection->get_Count(&certificateCollectionCount));

                        wil::com_ptr<ICoreWebView2ExperimentalClientCertificate> certificate = nullptr;

                        if (certificateCollectionCount > 0)
                        {
                            // There is no significance to the order, picking a certificate arbitrarily.
                            CHECK_FAILURE(certificateCollection->GetValueAtIndex(certificateCollectionCount - 1, &certificate));
                            // Continue with the selected certificate to respond to the server.
                            CHECK_FAILURE(args->put_SelectedCertificate(certificate.get()));
                            CHECK_FAILURE(args->put_Handled(TRUE));
                        }
                        else
                        {
                            //Continue without a certificate to respond to the server if certificate collection is empty.
                            CHECK_FAILURE(args->put_Handled(TRUE));
                        }
                        return S_OK;
                })
            .Get(),
                    &m_ClientCertificateRequestedToken));
    }
    else
    {
        CHECK_FAILURE(m_webViewExperimental->remove_ClientCertificateRequested(
            m_ClientCertificateRequestedToken));
        m_ClientCertificateRequestedToken.value = 0;
    }
}
```

```cpp
    m_webViewExperimental = m_webView.try_query<ICoreWebView2Experimental3>();
    if (m_webViewExperimental)
    {
        CHECK_FAILURE(m_webViewExperimental->add_ClientCertificateRequested(
            Callback<ICoreWebView2ExperimentalClientCertificateRequestedEventHandler>(
                [this](
                    ICoreWebView2* sender,
                    ICoreWebView2ExperimentalClientCertificateRequestedEventArgs* args) {
                        auto showDialog = [this, args] {
                            wil::com_ptr<ICoreWebView2ExperimentalClientCertificateCollection> certificateCollection;
                            CHECK_FAILURE(args->get_MutuallyTrustedCertificates(&certificateCollection));

                            wil::unique_cotaskmem_string host;
                            CHECK_FAILURE(args->get_Host(&host));

                            INT port = FALSE;
                            CHECK_FAILURE(args->get_Port(&port));

                            UINT certificateCollectionCount;
                            CHECK_FAILURE(certificateCollection->get_Count(&certificateCollectionCount));

                            wil::com_ptr<ICoreWebView2ExperimentalClientCertificate> certificate = nullptr;

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
```

#### remove_ClientCertificateRequested

Remove an event handler previously added with add_ClientCertificateRequested.

> public HRESULT [remove_ClientCertificateRequested](#remove_clientcertificaterequested)(EventRegistrationToken token)

#### COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND

Specifies the browser process exit type used in the ICoreWebView2ExperimentalBrowserProcessExitedEventArgs interface.

> enum [COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND](#corewebview2_browser_process_exit_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_NORMAL            | Indicates that the browser process ended normally.
COREWEBVIEW2_BROWSER_PROCESS_EXIT_KIND_FAILED            | Indicates that the browser process ended unexpectedly.

#### COREWEBVIEW2_CLIENT_CERTIFICATE_KIND

Specifies the client certificate kind.

> enum [COREWEBVIEW2_CLIENT_CERTIFICATE_KIND](#corewebview2_client_certificate_kind)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_SMART_CARD            | Specifies smart card certificate.
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_PIN            | Specifies PIN certificate.
COREWEBVIEW2_CLIENT_CERTIFICATE_KIND_OTHER            | Specifies other certificate.

#### COREWEBVIEW2_MATRIX_4X4

Matrix that represents a 3D transform.

> typedef [COREWEBVIEW2_MATRIX_4X4](#corewebview2_matrix_4x4)

This transform is used to calculate correct coordinates when calling CreateCoreWebView2PointerInfoFromPointerId. This is equivalent to a D2D1_MATRIX_4X4_F

#### COREWEBVIEW2_UPDATE_RUNTIME_STATUS

Status of UpdateRuntime operation result.

> enum [COREWEBVIEW2_UPDATE_RUNTIME_STATUS](#corewebview2_update_runtime_status)

 Values                         | Descriptions
--------------------------------|---------------------------------------------
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_LATEST_VERSION_INSTALLED            | Latest version of Edge WebView2 Runtime is installed.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_UPDATE_ALREADY_RUNNING            | Edge WebView2 Runtime update is already running, which could be triggered by auto update or by other UpdateRuntime request from some app.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_BLOCKED_BY_POLICY            | Edge WebView2 Runtime update is blocked by group policy.
COREWEBVIEW2_UPDATE_RUNTIME_STATUS_FAILED            | Edge WebView2 Runtime update failed.

