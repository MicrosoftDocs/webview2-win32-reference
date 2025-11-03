---
description: This interface manages shared workers in WebView2.
title: WebView2 Win32 C++ ICoreWebView2ExperimentalSharedWorkerManager
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2ExperimentalSharedWorkerManager
topic_type: 
- APIRef
api_name:
- ICoreWebView2ExperimentalSharedWorkerManager
- ICoreWebView2ExperimentalSharedWorkerManager.add_SharedWorkerCreated
- ICoreWebView2ExperimentalSharedWorkerManager.GetSharedWorkers
- ICoreWebView2ExperimentalSharedWorkerManager.remove_SharedWorkerCreated
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2ExperimentalSharedWorkerManager

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2ExperimentalSharedWorkerManager
  : public IUnknown
```

This interface manages shared workers in WebView2.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_SharedWorkerCreated](#add_sharedworkercreated) | Adds an event handler for the `SharedWorkerCreated` event.
[GetSharedWorkers](#getsharedworkers) | Gets a list of the shared workers created under the same profile.
[remove_SharedWorkerCreated](#remove_sharedworkercreated) | Removes an event handler previously added with `add_SharedWorkerCreated`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_SharedWorkerCreated

Adds an event handler for the `SharedWorkerCreated` event.

> public HRESULT [add_SharedWorkerCreated](#add_sharedworkercreated)([ICoreWebView2ExperimentalSharedWorkerCreatedEventHandler](icorewebview2experimentalsharedworkercreatedeventhandler.md#icorewebview2experimentalsharedworkercreatedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `SharedWorkerCreated` event.

A SharedWorker is a specific type of worker that can be accessed from several browsing contexts, such as multiple windows, iframes, or even other workers. Unlike Dedicated Workers, which have their own separate global scope, SharedWorkers share a common global scope called SharedWorkerGlobalScope.

This event is raised when a web application creates a shared worker using the `new SharedWorker("worker.js")` method. See the [Shared Worker](https://developer.mozilla.org/docs/Web/API/SharedWorker) for more information.

```cpp
    CHECK_FAILURE(m_sharedWorkerManager->add_SharedWorkerCreated(
        Callback<ICoreWebView2ExperimentalSharedWorkerCreatedEventHandler>(
            [this](
                ICoreWebView2ExperimentalSharedWorkerManager* sender,
                ICoreWebView2ExperimentalSharedWorkerCreatedEventArgs* args)
            {
                wil::com_ptr<ICoreWebView2ExperimentalSharedWorker> sharedWorker;
                CHECK_FAILURE(args->get_Worker(&sharedWorker));

                wil::unique_cotaskmem_string scriptUri;
                CHECK_FAILURE(sharedWorker->get_ScriptUri(&scriptUri));

                std::wstring scriptUriStr(scriptUri.get());
                m_appWindow->AsyncMessageBox(scriptUriStr, L"Shared worker is created");

                // Subscribe to worker destroying event
                sharedWorker->add_Destroying(
                    Callback<ICoreWebView2ExperimentalSharedWorkerDestroyingEventHandler>(
                        [this, scriptUriStr](
                            ICoreWebView2ExperimentalSharedWorker* sender,
                            IUnknown* args) -> HRESULT
                        {
                            /*Cleanup on worker destruction*/
                            m_appWindow->AsyncMessageBox(
                                scriptUriStr, L"Shared worker is destroyed");
                            return S_OK;
                        })
                        .Get(),
                    nullptr);

                return S_OK;
            })
            .Get(),
        &m_sharedWorkerCreatedToken));
```

#### GetSharedWorkers

Gets a list of the shared workers created under the same profile.

> public HRESULT [GetSharedWorkers](#getsharedworkers)([ICoreWebView2ExperimentalGetSharedWorkersCompletedHandler](icorewebview2experimentalgetsharedworkerscompletedhandler.md#icorewebview2experimentalgetsharedworkerscompletedhandler) * handler)

#### remove_SharedWorkerCreated

Removes an event handler previously added with `add_SharedWorkerCreated`.

> public HRESULT [remove_SharedWorkerCreated](#remove_sharedworkercreated)(EventRegistrationToken token)

