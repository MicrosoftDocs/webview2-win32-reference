---
description: This interface represents a shared worker in WebView2 and provides methods and properties for interacting with it, such as listening to destroying events, getting the script URI, origin, and top-level origin of the worker etc.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSharedWorker
ms.date: 08/04/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSharedWorker
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSharedWorker
- ICoreWebView2ExperimentalSharedWorker.add_Destroying
- ICoreWebView2ExperimentalSharedWorker.get_Origin
- ICoreWebView2ExperimentalSharedWorker.get_ScriptUri
- ICoreWebView2ExperimentalSharedWorker.get_TopLevelOrigin
- ICoreWebView2ExperimentalSharedWorker.remove_Destroying
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSharedWorker

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSharedWorker
  : public IUnknown
```

This interface represents a shared worker in WebView2 and provides methods and properties for interacting with it, such as listening to destroying events, getting the script URI, origin, and top-level origin of the worker etc.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_Destroying](#add_destroying) | Adds an event handler for the `Destroying` event.
[get_Origin](#get_origin) | A string representing the URI of the origin where the worker is executing.
[get_ScriptUri](#get_scripturi) | A string representing the Uri of the script that the worker is executing.
[get_TopLevelOrigin](#get_toplevelorigin) | A string representing the URI of the top-level document that the worker is associated with.
[remove_Destroying](#remove_destroying) | Removes an event handler previously added with `add_Destroying`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_Destroying

Adds an event handler for the `Destroying` event.

> public HRESULT [add_Destroying](#add_destroying)([ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler](icorewebview2experimentalsharedworkerdestroyingeventhandler.md#icorewebview2experimentalsharedworkerdestroyingeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `Destroying` event that is raised when the worker object is Destroying.

A worker object is Destroying when the worker script is terminated or when the `CoreWebView2SharedWorker` object is Destroying.

If the worker has already been destroyed before the event handler is registered, the handler will never be called.

#### get_Origin

A string representing the URI of the origin where the worker is executing.

> public HRESULT [get_Origin](#get_origin)(LPWSTR * value)

If a worker created with `ScriptUri` set to https://example.com/worker.js, the origin will be https://example.com/.

Refer to the Host Name Canonicalization for details on how normalization is performed.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_ScriptUri

A string representing the Uri of the script that the worker is executing.

> public HRESULT [get_ScriptUri](#get_scripturi)(LPWSTR * value)

The `scriptUri` is a fully qualified URI, including the scheme, host, and path. In contrast, the `scriptURL` property of the `Worker` object in the DOM returns the relative URL of the script being executed by the worker. For more details on DOM API, see the [DOM API documentation](https://developer.mozilla.org/docs/Web/API/Worker/scriptURL).

Refer to the Host Name Canonicalization for details on how normalization is performed. The same process applies to the `scriptURL` when a worker is created from DOM API. The `scriptUri` property reflects this normalization, ensuring that the URL is standardized. For example, `HTTPS://EXAMPLE.COM/worker.js` is canonicalized to `https://example.com/worker.js`; `https://b????cher.de/worker.js` is canonicalized to `https://xn--bcher-kva.de/worker.js`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### get_TopLevelOrigin

A string representing the URI of the top-level document that the worker is associated with.

> public HRESULT [get_TopLevelOrigin](#get_toplevelorigin)(LPWSTR * value)

If a worker is created with `ScriptUri` set to https://example.com/worker.js, the top-level origin is https://example.com/. If the same worker is created from a iframe at https://example.com/ which is hosted on https://example2.com/, the top-level origin is https://example2.com/.

Refer to the Host Name Canonicalization for details on how normalization is performed.

When CustomDataPartitionId is set, the `TopLevelOrigin` will be a generated site like guid.invalid. For example, if the top-level document is https://example.com/worker.js, the top-level origin will be https://guid.invalid/.

For more details see `ICoreWebView2Experimental20::CustomDataPartitionId`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### remove_Destroying

Removes an event handler previously added with `add_Destroying`.

> public HRESULT [remove_Destroying](#remove_destroying)(EventRegistrationToken token)

