---
description: A continuation of the ICoreWebView2 interface to manage dedicated workers.
title: WebView2 Win32 C++ ICoreWebView2Experimental30
ms.date: 11/03/2025
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Experimental30
topic_type: 
- APIRef
api_name:
- ICoreWebView2Experimental30
- ICoreWebView2Experimental30.add_DedicatedWorkerCreated
- ICoreWebView2Experimental30.remove_DedicatedWorkerCreated
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Experimental30

[!INCLUDE [deprecation-note](../includes/deprecation-note.md)]

[!INCLUDE [prerelease-note](../includes/prerelease-note.md)]

```
interface ICoreWebView2Experimental30
  : public IUnknown
```

A continuation of the [ICoreWebView2](icorewebview2.md#icorewebview2) interface to manage dedicated workers.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DedicatedWorkerCreated](#add_dedicatedworkercreated) | Adds an event handler for the `DedicatedWorkerCreated` event.
[remove_DedicatedWorkerCreated](#remove_dedicatedworkercreated) | Removes an event handler previously added with `add_DedicatedWorkerCreated`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3415

## Members

#### add_DedicatedWorkerCreated

Adds an event handler for the `DedicatedWorkerCreated` event.

> public HRESULT [add_DedicatedWorkerCreated](#add_dedicatedworkercreated)([ICoreWebView2ExperimentalDedicatedWorkerCreatedEventHandler](icorewebview2experimentaldedicatedworkercreatedeventhandler.md#icorewebview2experimentaldedicatedworkercreatedeventhandler) * eventHandler, EventRegistrationToken * token)

Subscribe to this event that gets raised when a new dedicated worker is created.

A Dedicated Worker is a type of web worker that allows you to run Javascript code in the background without blocking the main thread, making them useful for tasks like heavy computations, data processing, and parallel execution. It is "dedicated" because it is linked to a single parent document and cannot be shared with other scripts.

This event is raised when a web application creates a dedicated worker using the `new Worker("/worker.js")` method. See the [Worker](https://developer.mozilla.org/docs/Web/API/Worker/Worker) for more information.

```cpp
    m_appWindow->GetWebView()->QueryInterface(IID_PPV_ARGS(&m_webView2Experimental_30));
    CHECK_FEATURE_RETURN_EMPTY(m_webView2Experimental_30);

    CHECK_FAILURE(m_webView2Experimental_30->add_DedicatedWorkerCreated(
        Callback<ICoreWebView2ExperimentalDedicatedWorkerCreatedEventHandler>(
            [this](
                ICoreWebView2* sender,
                ICoreWebView2ExperimentalDedicatedWorkerCreatedEventArgs* args)
            {
                wil::com_ptr<ICoreWebView2ExperimentalDedicatedWorker> dedicatedWorker;
                CHECK_FAILURE(args->get_Worker(&dedicatedWorker));

                wil::unique_cotaskmem_string scriptUri;
                CHECK_FAILURE(dedicatedWorker->get_ScriptUri(&scriptUri));

                std::wstring scriptUriStr(scriptUri.get());
                m_appWindow->AsyncMessageBox(scriptUriStr, L"Dedicated worker is created");

                // Subscribe to worker destroying event
                dedicatedWorker->add_Destroying(
                    Callback<ICoreWebView2ExperimentalDedicatedWorkerDestroyingEventHandler>(
                        [this, scriptUriStr](
                            ICoreWebView2ExperimentalDedicatedWorker* sender,
                            IUnknown* args) -> HRESULT
                        {
                            /*Cleanup on worker destruction*/
                            m_appWindow->AsyncMessageBox(
                                scriptUriStr, L"Dedicated worker is destroyed");
                            return S_OK;
                        })
                        .Get(),
                    nullptr);

                return S_OK;
            })
            .Get(),
        &m_dedicatedWorkerCreatedToken));
```

#### remove_DedicatedWorkerCreated

Removes an event handler previously added with `add_DedicatedWorkerCreated`.

> public HRESULT [remove_DedicatedWorkerCreated](#remove_dedicatedworkercreated)(EventRegistrationToken token)

