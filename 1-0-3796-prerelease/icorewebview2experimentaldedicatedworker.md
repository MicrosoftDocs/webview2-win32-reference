---
description: This interface represents a dedicated worker in WebView2 and provides methods and properties for interacting with it, such as getting the script uri, posting messages, managing events related to the creation of child workers, termination etc.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalDedicatedWorker
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalDedicatedWorker
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalDedicatedWorker
- ICoreWebView2ExperimentalDedicatedWorker.add_DedicatedWorkerCreated
- ICoreWebView2ExperimentalDedicatedWorker.add_Destroying
- ICoreWebView2ExperimentalDedicatedWorker.add_WebMessageReceived
- ICoreWebView2ExperimentalDedicatedWorker.get_ScriptUri
- ICoreWebView2ExperimentalDedicatedWorker.PostWebMessageAsJson
- ICoreWebView2ExperimentalDedicatedWorker.PostWebMessageAsString
- ICoreWebView2ExperimentalDedicatedWorker.remove_DedicatedWorkerCreated
- ICoreWebView2ExperimentalDedicatedWorker.remove_Destroying
- ICoreWebView2ExperimentalDedicatedWorker.remove_WebMessageReceived
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalDedicatedWorker

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalDedicatedWorker
  : public IUnknown
```

This interface represents a dedicated worker in WebView2 and provides methods and properties for interacting with it, such as getting the script uri, posting messages, managing events related to the creation of child workers, termination etc.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DedicatedWorkerCreated](#add_dedicatedworkercreated) | Adds an event handler for the `DedicatedWorkerCreated` event.
[add_Destroying](#add_destroying) | Adds an event handler for the `Destroying` event.
[add_WebMessageReceived](#add_webmessagereceived) | Adds an event handler for the `WebMessageReceived` event.
[get_ScriptUri](#get_scripturi) | A string representing the Uri of the script that the worker is executing.
[PostWebMessageAsJson](#postwebmessageasjson) | Posts the specified webMessageAsJson to this worker.
[PostWebMessageAsString](#postwebmessageasstring) | Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.
[remove_DedicatedWorkerCreated](#remove_dedicatedworkercreated) | Removes an event handler previously added with `add_DedicatedWorkerCreated`.
[remove_Destroying](#remove_destroying) | Removes an event handler previously added with `add_Destroying`.
[remove_WebMessageReceived](#remove_webmessagereceived) | Removes an event handler previously added with `add_WebMessageReceived`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_DedicatedWorkerCreated

Adds an event handler for the `DedicatedWorkerCreated` event.

> public HRESULT [add_DedicatedWorkerCreated](#add_dedicatedworkercreated)([ICoreWebView2ExperimentalDedicatedWorkerDedicatedWorkerCreatedEventHandler](icorewebview2experimentaldedicatedworkerdedicatedworkercreatedeventhandler.md#icorewebview2experimentaldedicatedworkerdedicatedworkercreatedeventhandler) * eventHandler, EventRegistrationToken * token)

Subscribe to this event that gets raised when a new dedicated worker is created from a dedicated worker.

A Dedicated Worker is a type of web worker that allows you to run Javascript code in the background without blocking the main thread, making them useful for tasks like heavy computations, data processing, and parallel execution. It is "dedicated" because it is linked to a single parent document and cannot be shared with other scripts.

This event is raised when a dedicated creates a dedicated worker using the `new Worker("/worker.js")` method. See the [Worker](https://developer.mozilla.org/docs/Web/API/Worker/Worker) for more information.

#### add_Destroying

Adds an event handler for the `Destroying` event.

> public HRESULT [add_Destroying](#add_destroying)([ICoreWebView2ExperimentalDedicatedWorkerDestroyingEventHandler](icorewebview2experimentaldedicatedworkerdestroyingeventhandler.md#icorewebview2experimentaldedicatedworkerdestroyingeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `Destroying` event that is raised when the worker object is Destroying.

A worker object is Destroying when the worker script is terminated or when the `CoreWebView2DedicatedWorker` object is Destroying.

If the worker has already been destroyed before the event handler is registered, the handler will never be called.

#### add_WebMessageReceived

Adds an event handler for the `WebMessageReceived` event.

> public HRESULT [add_WebMessageReceived](#add_webmessagereceived)([ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler](icorewebview2experimentaldedicatedworkerwebmessagereceivedeventhandler.md#icorewebview2experimentaldedicatedworkerwebmessagereceivedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `WebMessageReceived` event. `WebMessageReceived` is fired, when the `ICoreWebView2Settings::IsWebMessageEnabled` setting is set TRUE and the worker runs `self.chrome.webview.postMessage`. The `postMessage` function is `void postMessage(object)` where object is any object supported by JSON conversion.

If the worker calls `postMessage` multiple times, the corresponding `WebMessageReceived` events are guaranteed to be fired in the same order.

```cpp
    dedicatedWorker->add_WebMessageReceived(
        Callback<ICoreWebView2ExperimentalDedicatedWorkerWebMessageReceivedEventHandler>(
            [this](
                ICoreWebView2ExperimentalDedicatedWorker* sender,
                ICoreWebView2WebMessageReceivedEventArgs* args) -> HRESULT
            {
                wil::unique_cotaskmem_string scriptUri;
                CHECK_FAILURE(args->get_Source(&scriptUri));

                wil::unique_cotaskmem_string messageRaw;
                CHECK_FAILURE(args->TryGetWebMessageAsString(&messageRaw));
                std::wstring messageFromWorker = messageRaw.get();

                std::wstringstream message{};
                message << L"Dedicated Worker: " << std::endl << scriptUri.get() << std::endl;
                message << std::endl;
                message << L"Message: " << std::endl << messageFromWorker << std::endl;
                m_appWindow->AsyncMessageBox(message.str(), L"Message from Dedicated Worker");

                return S_OK;
            })
            .Get(),
        nullptr);
```

#### get_ScriptUri

A string representing the Uri of the script that the worker is executing.

> public HRESULT [get_ScriptUri](#get_scripturi)(LPWSTR * value)

The `scriptUri` is a fully qualified URI, including the scheme, host, and path. In contrast, the `scriptURL` property of the `Worker` object in the DOM returns the relative URL of the script being executed by the worker. For more details on DOM API, see the [DOM API documentation](https://developer.mozilla.org/docs/Web/API/Worker/scriptURL).

Refer to the Host Name Canonicalization for details on how normalization is performed. The same process applies to the `scriptURL` when a worker is created from DOM API. The `scriptUri` property reflects this normalization, ensuring that the URL is standardized. For example, `HTTPS://EXAMPLE.COM/worker.js` is canonicalized to `https://example.com/worker.js`; `https://b????cher.de/worker.js` is canonicalized to `https://xn--bcher-kva.de/worker.js`.

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
`ICoreWebView2ServiceWorker::PostWebMessageAsJson`.
```

```cpp
    // Do not block from event handler
    m_appWindow->RunAsync(
        [this, dedicatedWorker]
        {
            TextInputDialog dialog(
                m_appWindow->GetMainWindow(), L"Post Web Message JSON", L"Web message JSON",
                L"Enter the web message as JSON.",
                L"{\"command\":\"ADD\",\"first\":2,\"second\":3}");
            // Ex: {"command":"ADD","first":2,"second":3}
            if (dialog.confirmed)
            {
                dedicatedWorker->PostWebMessageAsJson(dialog.input.c_str());
            }
        });
```

#### PostWebMessageAsString

Posts a message that is a simple string rather than a JSON string representation of a JavaScript object.

> public HRESULT [PostWebMessageAsString](#postwebmessageasstring)(LPCWSTR webMessageAsString)

This behaves exactly the same manner as `PostWebMessageAsJson`, but the `data` property of the event arg of the `self.chrome.webview` message is a string with the same value as `webMessageAsString`. Use this instead of `PostWebMessageAsJson` if you want to communicate using simple strings rather than JSON objects. Please see `PostWebMessageAsJson` for additional information. 
```cpp
See also the equivalent methods: `ICoreWebView2::PostWebMessageAsString`,
`ICoreWebView2Frame::PostWebMessageAsString`,
`ICoreWebView2ServiceWorker::PostWebMessageAsString`.
```

#### remove_DedicatedWorkerCreated

Removes an event handler previously added with `add_DedicatedWorkerCreated`.

> public HRESULT [remove_DedicatedWorkerCreated](#remove_dedicatedworkercreated)(EventRegistrationToken token)

#### remove_Destroying

Removes an event handler previously added with `add_Destroying`.

> public HRESULT [remove_Destroying](#remove_destroying)(EventRegistrationToken token)

#### remove_WebMessageReceived

Removes an event handler previously added with `add_WebMessageReceived`.

> public HRESULT [remove_WebMessageReceived](#remove_webmessagereceived)(EventRegistrationToken token)

