---
description: A continuation of the ICoreWebView2Frame interface to manage dedicated workers.
title: WebView2 Win32 C++ ICoreWebView2Frame8
ms.date: 05/04/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2Frame8
topic_type: 
- APIRef
api_name:
- ICoreWebView2Frame8
- ICoreWebView2Frame8.add_DedicatedWorkerCreated
- ICoreWebView2Frame8.remove_DedicatedWorkerCreated
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2Frame8

```
interface ICoreWebView2Frame8
  : public ICoreWebView2Frame7
```

A continuation of the [ICoreWebView2Frame](icorewebview2frame.md#icorewebview2frame) interface to manage dedicated workers.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DedicatedWorkerCreated](#add_dedicatedworkercreated) | Adds an event handler for the `DedicatedWorkerCreated` event.
[remove_DedicatedWorkerCreated](#remove_dedicatedworkercreated) | Removes an event handler previously added with `add_DedicatedWorkerCreated`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    

## Members

#### add_DedicatedWorkerCreated

Adds an event handler for the `DedicatedWorkerCreated` event.

> public HRESULT [add_DedicatedWorkerCreated](#add_dedicatedworkercreated)([ICoreWebView2FrameDedicatedWorkerCreatedEventHandler](icorewebview2framededicatedworkercreatedeventhandler.md#icorewebview2framededicatedworkercreatedeventhandler) * eventHandler, EventRegistrationToken * token)

Subscribe to this event that gets raised when a new dedicated worker is created from an iframe.

A Dedicated Worker is a type of web worker that allows you to run Javascript code in the background without blocking the main thread, making them useful for tasks like heavy computations, data processing, and parallel execution. It is "dedicated" because it is linked to a single parent document and cannot be shared with other scripts.

This event is raised when a web application creates a dedicated worker using the `new Worker("/worker.js")` method. See the [Worker](https://developer.mozilla.org/docs/Web/API/Worker/Worker) for more information.

#### remove_DedicatedWorkerCreated

Removes an event handler previously added with `add_DedicatedWorkerCreated`.

> public HRESULT [remove_DedicatedWorkerCreated](#remove_dedicatedworkercreated)(EventRegistrationToken token)

