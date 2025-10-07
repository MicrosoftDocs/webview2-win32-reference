---
description: This interface represents a service worker in WebView2 and provides methods and properties for interacting with it, such as getting the script uri, posting messages to it etc.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalServiceWorker
ms.date: 09/01/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalServiceWorker
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalServiceWorker
- ICoreWebView2ExperimentalServiceWorker.add_Destroying
- ICoreWebView2ExperimentalServiceWorker.add_WebMessageReceived
- ICoreWebView2ExperimentalServiceWorker.get_ScriptUri
- ICoreWebView2ExperimentalServiceWorker.PostWebMessageAsJson
- ICoreWebView2ExperimentalServiceWorker.PostWebMessageAsString
- ICoreWebView2ExperimentalServiceWorker.remove_Destroying
- ICoreWebView2ExperimentalServiceWorker.remove_WebMessageReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalServiceWorker

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalServiceWorker
  : public IUnknown
```

This interface represents a service worker in WebView2 and provides methods and properties for interacting with it, such as getting the script uri, posting messages to it etc.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_Destroying](#add_destroying) | Adds an event handler for the `Destroying` event.
[add_WebMessageReceived](#add_webmessagereceived) | Adds an event handler for the `WebMessageReceived` event.
[get_ScriptUri](#get_scripturi) | A string representing the Uri of the script that the worker is executing.
[PostWebMessageAsJson](#postwebmessageasjson) | Posts the specified webMessageAsJson to this worker.
[PostWebMessageAsString](#postwebmessageasstring) | Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.
[remove_Destroying](#remove_destroying) | Removes an event handler previously added with `add_Destroying`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Removes an event handler previously added with `add_WebMessageReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_Destroying

Adds an event handler for the `Destroying` event.

> public HRESULT [add_Destroying](#add_destroying)([ICoreWebView2ExperimentalServiceWorkerDestroyingEventHandler](icorewebview2experimentalserviceworkerdestroyingeventhandler.md#icorewebview2experimentalserviceworkerdestroyingeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `Destroying` event that is raised when the worker object is Destroying.

A worker object is Destroying when the worker script is terminated or when the `CoreWebView2ServiceWorker` object is Destroying.

If the worker has already been destroyed before the event handler is registered, the handler will never be called.

#### add_WebMessageReceived

Adds an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler](icorewebview2experimentalserviceworkerwebmessagereceivedeventhandler.md#icorewebview2experimentalserviceworkerwebmessagereceivedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `WebMessageReceived` event. `WebMessageReceived` is fired, when the `ICoreWebView2Settings::IsWebMessageEnabled` setting is set TRUE and the worker runs `self.chrome.webview.postMessage`. The `postMessage` function is `void postMessage(object)` where object is any object supported by JSON conversion.

If the worker calls `postMessage` multiple times, the corresponding `WebMessageReceived` events are guaranteed to be fired in the same order.

```cpp
    serviceWorker->add_WebMessageReceived(
        Callback<ICoreWebView2ExperimentalServiceWorkerWebMessageReceivedEventHandler>(
            [this](
                ICoreWebView2ExperimentalServiceWorker* sender,
                ICoreWebView2WebMessageReceivedEventArgs* args) -> HRESULT
            {
                wil::unique_cotaskmem_string scriptUri;
                CHECK_FAILURE(args->get_Source(&scriptUri));

                wil::unique_cotaskmem_string messageRaw;
                CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
                std::wstring messageFromWorker = messageRaw.get();

                std::wstringstream message{};
                message << L"Service Worker: " << std::endl << scriptUri.get() << std::endl;
                message << std::endl;
                message << L"Message: " << std::endl << messageFromWorker << std::endl;
                m_appWindow->AsyncMessageBox(message.str(), L"Message from Service Worker");

                return S_OK;
            })
            .Get(),
        nullptr);
```

#### get_ScriptUri

A string representing the Uri of the script that the worker is executing.

> public HRESULT [get_ScriptUri](#get_scripturi)(LPWSTR * value)

The `scriptUri` is a fully qualified URI, including the scheme, host, and path. In contrast, the `scriptURL` property of the `Worker` object in the DOM returns the relative URL of the script being executed by the worker. For more details on DOM API, see the [DOM API documentation](https://developer.mozilla.org/docs/Web/API/Worker/scriptURL).

Refer to the Host Name Canonicalization for details on how normalization is performed. The same process applies to the `scriptURL` when a worker is registered from DOM API. The `scriptUri` property reflects this normalization, ensuring that the URL is standardized. For example, `HTTPS://EXAMPLE.COM/worker.js` is canonicalized to `https://example.com/worker.js`; `https://b????cher.de/worker.js` is canonicalized to `https://xn--bcher-kva.de/worker.js`.

The caller must free the returned string with `CoTaskMemFree`. See [API Conventions](/microsoft-edge/webview2/concepts/win32-api-conventions#strings).

#### PostWebMessageAsJson

Posts the specified webMessageAsJson to this worker.

> public HRESULT [PostWebMessageAsJson](#postwebmessageasjson)(LPCWSTR webMessageAsJson)

The worker receives the message by subscribing to the `message` event of the `self.chrome.webview` of the worker.

```cpp
self.chrome.webview.addEventListener('message', handler)
self.chrome.webview.removeEventListener('message', handler)
```

The event args is an instance of `MessageEvent`. The `ICoreWebView2Settings::IsWebMessageEnabled` setting must be `TRUE` or the web message will not be sent. The `data` property of the event arg is the `webMessageAsJson` string parameter parsed as a JSON string into a JS object. The `source` property of the event arg is the path to the worker script. The message is delivered asynchronously. If the worker is terminated or destroyed before the message is posted, the message is discarded. Worker Javascript may subscribe and unsubscribe to the event using the following code: 
```js
self.chrome.webview.addEventListener('message', handler)
self.chrome.webview.removeEventListener('message', handler)
```

```cpp
See also the equivalent methods: `ICoreWebView2::PostWebMessageAsJson`,
`ICoreWebView2Frame::PostWebMessageAsJson`,
`ICoreWebView2DedicatedWorker::PostWebMessageAsJson`.
```

```cpp
    std::wstring msg = L"{\"command\":\"ADD_TO_CACHE\",\"url\":\"" + url + L"\"}";
    serviceWorker->PostWebMessageAsJson(msg.c_str());
```

#### PostWebMessageAsString

Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

This behaves exactly the same manner as `PostWebMessageAsJson`, but the `data` property of the event arg of the `self.chrome.webview` message is a string with the same value as `webMessageAsString`. Use this instead of `PostWebMessageAsJson` if you want to communicate using simple strings rather than JSON objects. Please see `PostWebMessageAsJson` for additional information. 
```cpp
See also the equivalent methods: `ICoreWebView2::PostWebMessageAsString`
`ICoreWebView2Frame::PostWebMessageAsString`,
`ICoreWebView2DedicatedWorker::PostWebMessageAsString`.
```

#### remove_Destroying

Removes an event handler previously added with `add_Destroying`.

> public HRESULT [remove_Destroying](#remove_destroying)(EventRegistrationToken token)

#### remove_WebMessageReceived

Removes an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

