---
description: This interface manages shared workers in WebView2.
title: WebView2 Win32 C++ ICoreWebView2SharedWorkerManager
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2SharedWorkerManager
topic_type: 
- APIRef
api_name:
- ICoreWebView2SharedWorkerManager
- ICoreWebView2SharedWorkerManager.add_SharedWorkerCreated
- ICoreWebView2SharedWorkerManager.GetSharedWorkers
- ICoreWebView2SharedWorkerManager.remove_SharedWorkerCreated
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2SharedWorkerManager

```
interface ICoreWebView2SharedWorkerManager
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
WebView2 Win32 Prerelease |    

## Members

#### add_SharedWorkerCreated

Adds an event handler for the `SharedWorkerCreated` event.

> public HRESULT [add_SharedWorkerCreated](#add_sharedworkercreated)([ICoreWebView2SharedWorkerCreatedEventHandler](icorewebview2sharedworkercreatedeventhandler.md#icorewebview2sharedworkercreatedeventhandler) * eventHandler, EventRegistrationToken * token)

Add an event handler for the `SharedWorkerCreated` event.

A SharedWorker is a specific type of worker that can be accessed from several browsing contexts, such as multiple windows, iframes, or even other workers. Unlike Dedicated Workers, which have their own separate global scope, SharedWorkers share a common global scope called SharedWorkerGlobalScope.

This event is raised when a web application creates a shared worker using the `new SharedWorker("worker.js")` method. See the [Shared Worker](https://developer.mozilla.org/docs/Web/API/SharedWorker) for more information.

```cpp
    CHECK_FAILURE(m_sharedWorkerManager->add_SharedWorkerCreated(
        Callback<ICoreWebView2SharedWorkerCreatedEventHandler>(
            [this](
                ICoreWebView2SharedWorkerManager* sender,
                ICoreWebView2SharedWorkerCreatedEventArgs* args)
            {
                wil::com_ptr<ICoreWebView2SharedWorker> sharedWorker;
                CHECK_FAILURE(args->get_Worker(&sharedWorker));

                wil::unique_cotaskmem_string scriptUri;
                CHECK_FAILURE(sharedWorker->get_ScriptUri(&scriptUri));

                std::wstring scriptUriStr(scriptUri.get());
                m_appWindow->AsyncMessageBox(scriptUriStr, L"Shared worker is created");

                // Subscribe to worker destroying event
                sharedWorker->add_Destroying(
                    Callback<ICoreWebView2SharedWorkerDestroyingEventHandler>(
                        [this, scriptUriStr](
                            ICoreWebView2SharedWorker* sender, IUnknown* args) -> HRESULT
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

> public HRESULT [GetSharedWorkers](#getsharedworkers)([ICoreWebView2GetSharedWorkersCompletedHandler](icorewebview2getsharedworkerscompletedhandler.md#icorewebview2getsharedworkerscompletedhandler) * handler)

#### remove_SharedWorkerCreated

Removes an event handler previously added with `add_SharedWorkerCreated`.

> public HRESULT [remove_SharedWorkerCreated](#remove_sharedworkercreated)(EventRegistrationToken token)

