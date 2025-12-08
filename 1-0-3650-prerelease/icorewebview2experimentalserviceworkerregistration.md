---
description: This interface represents a service worker registration in WebView2 and provides methods and properties for interacting with it, such as getting the scope uri, active service worker, listening for service worker activation, unregistering events etc.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorkerRegistration
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorkerRegistration
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorkerRegistration
- ICoreWebView2ExperimentalServiceWorkerRegistration.add_ServiceWorkerActivated
- ICoreWebView2ExperimentalServiceWorkerRegistration.add_Unregistering
- ICoreWebView2ExperimentalServiceWorkerRegistration.get_ActiveServiceWorker
- ICoreWebView2ExperimentalServiceWorkerRegistration.get_Origin
- ICoreWebView2ExperimentalServiceWorkerRegistration.get_ScopeUri
- ICoreWebView2ExperimentalServiceWorkerRegistration.get_TopLevelOrigin
- ICoreWebView2ExperimentalServiceWorkerRegistration.remove_ServiceWorkerActivated
- ICoreWebView2ExperimentalServiceWorkerRegistration.remove_Unregistering
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorkerRegistration

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorkerRegistration
  : public IUnknown
```

This interface represents a service worker registration in WebView2 and provides methods and properties for interacting with it, such as getting the scope uri, active service worker, listening for service worker activation, unregistering events etc.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_ServiceWorkerActivated](#add_serviceworkeractivated) | Adds an event handler for the `ServiceWorkerActivated` event.
[add_Unregistering](#add_unregistering) | Adds an event handler for the `Unregistering` event.
[get_ActiveServiceWorker](#get_activeserviceworker) | The active service worker that was created.
[get_Origin](#get_origin) | A string representing the URI of the origin where the worker is executing.
[get_ScopeUri](#get_scopeuri) | The `scopeUri` is a fully qualified URI, including the scheme, host and path, that specifies the range of URLs a service worker can control.
[get_TopLevelOrigin](#get_toplevelorigin) | A string representing the URI of the top-level document that the worker is associated with.
[remove_ServiceWorkerActivated](#remove_serviceworkeractivated) | Removes an event handler previously added with `add_ServiceWorkerActivated`.
[remove_Unregistering](#remove_unregistering) | Removes an event handler previously added with `add_Unregistering`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_ServiceWorkerActivated

Adds an event handler for the `ServiceWorkerActivated` event.

> public HRESULT [add_ServiceWorkerActivated](#add_serviceworkeractivated)([ICoreWebView2ExperimentalServiceWorkerActivatedEventHandler](icorewebview2experimentalserviceworkeractivatedeventhandler.md#icorewebview2experimentalserviceworkeractivatedeventhandler) * eventHandler, EventRegistrationToken * token)

Adds an event handler for the `ServiceWorkerActivated` event.

This event is raised when a service worker is activated. A service worker is activated when its script has been successfully registered and it is ready to control the pages within the scope of the registration.

This event is also raised when an updated version of a service worker reaches the active state. In such a case, the existing CoreWebView2ServiceWorker object is destroying, and this event is raised with a new CoreWebView2ServiceWorker object representing the updated service worker. The active service worker is the one that receives fetch and message events for the pages it controls. See the [Service Worker](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerRegistration/active) documentation for more information.

If you register for the `ServiceWorkerActivated` event and the registration already has an active worker, the event handler is not called immediately. Instead, it waits for the next activation event to occur. Therefore, you should first check if an active service worker is running by using the `ActiveServiceWorker` property.

#### add_Unregistering

Adds an event handler for the `Unregistering` event.

> public HRESULT [add_Unregistering](#add_unregistering)([ICoreWebView2ExperimentalServiceWorkerRegistrationUnregisteringEventHandler](icorewebview2experimentalserviceworkerregistrationunregisteringeventhandler.md#icorewebview2experimentalserviceworkerregistrationunregisteringeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `Unregistering` event that is raised when the worker registration is unregistered using the JS api `registration.unregister()`. See the [Unregister](https://developer.mozilla.org/docs/Web/API/ServiceWorkerRegistration/unregister) for more information.

#### get_ActiveServiceWorker

The active service worker that was created.

> public HRESULT [get_ActiveServiceWorker](#get_activeserviceworker)([ICoreWebView2ExperimentalServiceWorker](icorewebview2experimentalserviceworker.md#icorewebview2experimentalserviceworker) ** value)

If there is no active service worker, it returns a null pointer. The active service worker is the service worker that controls the pages within the scope of the registration. See the [Service Worker] (https://developer.mozilla.org/docs/Web/API/ServiceWorker) for more information.

This corresponds to the `active` property of the `ServiceWorkerRegistration` object in the DOM. For more information, see the [MDN documentation] (https://developer.mozilla.org/docs/Web/API/ServiceWorkerRegistration/active).

#### get_Origin

A string representing the URI of the origin where the worker is executing.

> public HRESULT [get_Origin](#get_origin)(LPWSTR * value)

If a worker created with `ScriptUri` set to https://example.com/worker.js, the origin will be https://example.com/.

Refer to the Host Name Canonicalization for details on how normalization is performed.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ScopeUri

The `scopeUri` is a fully qualified URI, including the scheme, host and path, that specifies the range of URLs a service worker can control.

> public HRESULT [get_ScopeUri](#get_scopeuri)(LPWSTR * value)

When registering a service worker, if no scope is specified, it defaults to the directory where the service worker script resides. For example, if the script is located at https://example.com/app/sw.js, the default `scopeUri` would be https://example.com/app/. However, if a scope is provided, it is defined relative to the application's base URI. For instance, if an application at https://example.com/ registers a service worker with a scope of /app/, the resulting `scopeUri` is https://example.com/app/.

Refer to the Host Name Canonicalization for details on how normalization is performed. The same process applies to the `Scope` when a service worker is registered from DOM API. The `scopeUri` property reflects this normalization, ensuring that the URI is standardized. For example, `HTTPS://EXAMPLE.COM/app/` is canonicalized to `https://example.com/app/`; `https://b????cher.de/` is canonicalized to `https://xn--bcher-kva.de/`.

The `scope` property of the `ServiceWorkerRegistration` object in the DOM returns the relative URL based on the application's base URI, while this property always returns a fully qualified URI. For more information on DOM API, see the [MDN documentation](https://developer.mozilla.org/docs/Web/API/ServiceWorkerRegistration/scope).

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_TopLevelOrigin

A string representing the URI of the top-level document that the worker is associated with.

> public HRESULT [get_TopLevelOrigin](#get_toplevelorigin)(LPWSTR * value)

If a worker is created with `ScriptUri` set to https://example.com/worker.js, the top-level origin is https://example.com/. If the same worker is created from a iframe at https://example.com/ which is hosted on https://example2.com/, the top-level origin is https://example2.com/.

Refer to the Host Name Canonicalization for details on how normalization is performed.

When CustomDataPartitionId is set, the `TopLevelOrigin` will be a generated site like guid.invalid. For example, if the top-level document is https://example.com/worker.js, the top-level origin will be `https://guid.invalid/`.

For more details see `ICoreWebView2Experimental20::CustomDataPartitionId`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### remove_ServiceWorkerActivated

Removes an event handler previously added with `add_ServiceWorkerActivated`.

> public HRESULT [remove_ServiceWorkerActivated](#remove_serviceworkeractivated)(EventRegistrationToken token)

#### remove_Unregistering

Removes an event handler previously added with `add_Unregistering`.

> public HRESULT [remove_Unregistering](#remove_unregistering)(EventRegistrationToken token)

