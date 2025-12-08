---
description: This interface manages registrations for service workers in WebView2.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerManager
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerManager
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerManager
- ICoreWebView2ExperimentalServiceWorkerManager.add_ServiceWorkerRegistered
- ICoreWebView2ExperimentalServiceWorkerManager.GetServiceWorkerRegistrations
- ICoreWebView2ExperimentalServiceWorkerManager.GetServiceWorkerRegistrationsForScope
- ICoreWebView2ExperimentalServiceWorkerManager.remove_ServiceWorkerRegistered
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerManager

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerManager
  : public IUnknown
```

This interface manages registrations for service workers in WebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ServiceWorkerRegistered](#add_serviceworkerregistered) | Adds an event handler for the `ServiceWorkerRegistered` event.
[GetServiceWorkerRegistrations](#getserviceworkerregistrations) | Gets a list of the service worker registrations under the same profile.
[GetServiceWorkerRegistrationsForScope](#getserviceworkerregistrationsforscope) | Gets the service worker registrations associated with the specified scope.
[remove_ServiceWorkerRegistered](#remove_serviceworkerregistered) | Removes an event handler previously added with `add_ServiceWorkerRegistered`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_ServiceWorkerRegistered

Adds an event handler for the `ServiceWorkerRegistered` event.

> public HRESULT [add_ServiceWorkerRegistered](#add_serviceworkerregistered)([ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler](icorewebview2experimentalserviceworkerregisteredeventhandler.md#icorewebview2experimentalserviceworkerregisteredeventhandler) * eventHandler, EventRegistrationToken * token)

A ServiceWorker is a specific type of worker that takes a JavaScript file that can control the web-page/site that it is associated with, intercepting and modifying navigation and resource requests, and caching resources in a very granular fashion to give you complete control over how app behaves in certain situations.

Service workers essentially act as proxy servers that sit between web applications, the browser, and the network (when available). They run in a different context from the web page, which means they have no direct access to the DOM. Unlike dedicated and shared workers, which may have direct access to a global scope shared with other scripts, service workers operate in isolation from the DOM, ensuring a more secure and controlled environment.

This event is raised when a web application registers a service worker using the `navigator.serviceWorker.register("/sw.js")` method. See the [Service Worker Registration](https://developer.mozilla.org/docs/Web/API/ServiceWorkerRegistration) for more information.

```cpp
    CHECK_FAILURE(m_serviceWorkerManager->add_ServiceWorkerRegistered(
        Callback<ICoreWebView2ExperimentalServiceWorkerRegisteredEventHandler>(
            [this](
                ICoreWebView2ExperimentalServiceWorkerManager* sender,
                ICoreWebView2ExperimentalServiceWorkerRegisteredEventArgs* args)
            {
                wil::com_ptr<ICoreWebView2ExperimentalServiceWorkerRegistration>
                    serviceWorkerRegistration;
                CHECK_FAILURE(args->get_ServiceWorkerRegistration(&serviceWorkerRegistration));

                if (serviceWorkerRegistration)
                {
                    wil::unique_cotaskmem_string scopeUri;
                    CHECK_FAILURE(serviceWorkerRegistration->get_ScopeUri(&scopeUri));
                    std::wstring scopeUriStr(scopeUri.get());

                    wil::unique_cotaskmem_string origin;
                    CHECK_FAILURE(serviceWorkerRegistration->get_Origin(&origin));

                    wil::unique_cotaskmem_string topLevelOrigin;
                    CHECK_FAILURE(
                        serviceWorkerRegistration->get_TopLevelOrigin(&topLevelOrigin));

                    // Subscribe to worker registration unregistering event
                    serviceWorkerRegistration->add_Unregistering(
                        Callback<
                            ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler>(
                            [this, scopeUriStr](
                                ICoreWebView2ExperimentalServiceWorkerRegistration* sender,
                                IUnknown* args) -> HRESULT
                            {
                                /*Cleanup on worker registration destruction*/
                                m_appWindow->AsyncMessageBox(
                                    scopeUriStr, L"Service worker is unregistered");
                                return S_OK;
                            })
                            .Get(),
                        nullptr);

                    wil::com_ptr<ICoreWebView2ExperimentalServiceWorker> serviceWorker;
                    CHECK_FAILURE(
                        serviceWorkerRegistration->get_ActiveServiceWorker(&serviceWorker));

                    if (serviceWorker)
                    {
                        wil::unique_cotaskmem_string scriptUri;
                        CHECK_FAILURE(serviceWorker->get_ScriptUri(&scriptUri));
                        std::wstring scriptUriStr(scriptUri.get());

                        // Subscribe to worker destroying event
                        serviceWorker->add_Destroying(
                            Callback<
                                ICoreWebView2ExperimentalServiceWorkerDestroyingEventHandler>(
                                [this, scriptUriStr](
                                    ICoreWebView2ExperimentalServiceWorker* sender,
                                    IUnknown* args) -> HRESULT
                                {
                                    /*Cleanup on worker destruction*/
                                    m_appWindow->AsyncMessageBox(
                                        scriptUriStr, L"Service worker is destroyed");
                                    return S_OK;
                                })
                                .Get(),
                            nullptr);
                    }
                    else
                    {
                        CHECK_FAILURE(serviceWorkerRegistration->add_ServiceWorkerActivated(
                            Callback<
                                ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler>(
                                [this](
                                    ICoreWebView2ExperimentalServiceWorkerRegistration* sender,
                                    ICoreWebView2ExperimentalServiceWorkerActivatedEventArgs*
                                        args) -> HRESULT
                                {
                                    wil::com_ptr<ICoreWebView2ExperimentalServiceWorker>
                                        serviceWorker;
                                    CHECK_FAILURE(
                                        args->get_ActiveServiceWorker(&serviceWorker));
                                    wil::unique_cotaskmem_string scriptUri;
                                    CHECK_FAILURE(serviceWorker->get_ScriptUri(&scriptUri));
                                    std::wstring scriptUriStr(scriptUri.get());

                                    // Subscribe to worker destroying event
                                    serviceWorker->add_Destroying(
                                        Callback<
                                            ICoreWebView2ExperimentalServiceWorkerDestroyingEventHandler>(
                                            [this, scriptUriStr](
                                                ICoreWebView2ExperimentalServiceWorker* sender,
                                                IUnknown* args) -> HRESULT
                                            {
                                                /*Cleanup on worker destruction*/
                                                m_appWindow->AsyncMessageBox(
                                                    scriptUriStr,
                                                    L"Service worker is destroyed");
                                                return S_OK;
                                            })
                                            .Get(),
                                        nullptr);

                                    m_appWindow->AsyncMessageBox(
                                        L"Service worker is activated", L"Service worker");

                                    return S_OK;
                                })
                                .Get(),
                            nullptr));
                    }

                    m_appWindow->AsyncMessageBox(scopeUriStr, L"Service worker is registered");
                }

                return S_OK;
            })
            .Get(),
        &m_serviceWorkerRegisteredToken));
```

#### GetServiceWorkerRegistrations

Gets a list of the service worker registrations under the same profile.

> public HRESULT [GetServiceWorkerRegistrations](#getserviceworkerregistrations)([ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler](icorewebview2experimentalgetserviceworkerregistrationscompletedhandler.md#icorewebview2experimentalgetserviceworkerregistrationscompletedhandler) * handler)

This method returns a list of `CoreWebView2ServiceWorkerRegistration` objects, each representing a service worker registration.

This method corresponds to the `getRegistrations` method of the `ServiceWorkerContainer` object in the DOM which returns a Promise that resolves to an array of `ServiceWorkerRegistration` objects. See the [MDN documentation] (https://developer.mozilla.org/docs/Web/API/ServiceWorkerContainer/getRegistrations) for more information.

#### GetServiceWorkerRegistrationsForScope

Gets the service worker registrations associated with the specified scope.

> public HRESULT [GetServiceWorkerRegistrationsForScope](#getserviceworkerregistrationsforscope)(LPCWSTR scopeUri, [ICoreWebView2ExperimentalGetServiceWorkerRegistrationsCompletedHandler](icorewebview2experimentalgetserviceworkerregistrationscompletedhandler.md#icorewebview2experimentalgetserviceworkerregistrationscompletedhandler) * handler)

If a service worker has been registered for the given scope, it gets the list of `CoreWebView2ServiceWorkerRegistration` objects otherwise returns empty list.

If the service worker is registered with a `scope` of '/app/' for an application at https://example.com/, you should specify the full qualified URI i.e., https://example.com/app/ when calling this method. If the scope was not explicitly specified during registration, you should use the directory where the service worker script resides, for example, https://example.com/app/.

Refer to the Host Name Canonicalization for details on how provided `scriptUri` normalization is performed. For example, `HTTPS://m????nchen.de/` will be normalized to `https://www.xn--kfk.com` for comparison.

This corresponds to the `getRegistration` method of the `ServiceWorkerContainer` object in the DOM which returns a Promise that resolves to a `ServiceWorkerRegistration` object. See the [MDN documentation] (https://developer.mozilla.org/docs/Web/API/ServiceWorkerContainer/getRegistration) for more information.

If scopeUri is empty string or null or invalid, the completed handler immediately returns `E_INVALIDARG` and with a null pointer.

#### remove_ServiceWorkerRegistered

Removes an event handler previously added with `add_ServiceWorkerRegistered`.

> public HRESULT [remove_ServiceWorkerRegistered](#remove_serviceworkerregistered)(EventRegistrationToken token)

