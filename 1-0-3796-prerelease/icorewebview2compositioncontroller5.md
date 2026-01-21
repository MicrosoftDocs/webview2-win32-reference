---
description: A continuation of the ICoreWebView2CompositionController4 interface.
title: WebView2 Win32 C++ ICoreWebView2CompositionController5
ms.date: 01/13/2026
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2CompositionController5
topic_type: 
- APIRef
api_name:
- ICoreWebView2CompositionController5
- ICoreWebView2CompositionController5.add_DragStarting
- ICoreWebView2CompositionController5.remove_DragStarting
api_type:
- COM
api_location:
- embeddedbrowserwebview.dll
---

# interface ICoreWebView2CompositionController5

```
interface ICoreWebView2CompositionController5
  : public ICoreWebView2CompositionController4
```

A continuation of the [ICoreWebView2CompositionController4](icorewebview2compositioncontroller4.md#icorewebview2compositioncontroller4) interface.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DragStarting](#add_dragstarting) | Adds an event handler for the `DragStarting` event.
[remove_DragStarting](#remove_dragstarting) | Removes an event handler previously added with `add_DragStarting`.

This interface includes an API which exposes the DragStarting event.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    N/A
WebView2 Win32 Prerelease |    1.0.3712

## Members

#### add_DragStarting

Adds an event handler for the `DragStarting` event.

> public HRESULT [add_DragStarting](#add_dragstarting)([ICoreWebView2DragStartingEventHandler](icorewebview2dragstartingeventhandler.md#icorewebview2dragstartingeventhandler) * eventHandler, EventRegistrationToken * token)

`DragStarting` is a deferrable event that is raised when the WebView2 detects a drag started within the WebView2. WebView2's default drag behavior is to synchronously call DoDragDrop when it detects drag. This event's args expose the data WebView2 uses to call DoDragDrop to allow users to implement their own drag logic and override WebView2's. Handlers of this event must set the `Handled` event to true in order to override WebView2's default logic. When invoking drag logic asynchronously using a deferral, handlers must take care to follow these steps in order:

* Invoke asynchronous drag logic

* Set the event args `Handled` property true

* Complete the deferral In the asynchronous case, WebView2 decides whether or not to invoke its default drag logic when the deferral completes. So the event args' `Handled` property must be true when the deferral is completed. 
```cpp
    // Using DragStarting to simply make a synchronous DoDragDrop call instead of
    // having WebView2 do it.
    CHECK_FAILURE(m_compController5->add_DragStarting(
        Callback<ICoreWebView2DragStartingEventHandler>(
            [this](
                ICoreWebView2CompositionController* sender,
                ICoreWebView2DragStartingEventArgs* args)
            {
                if (m_dragOverrideMode != DragOverrideMode::OVERRIDE)
                {
                    // If the event is marked handled, WebView2 will not execute its drag logic.
                    args->put_Handled(m_dragOverrideMode == DragOverrideMode::NOOP);
                    return S_OK;
                }

                wil::com_ptr<IDataObject> dragData;
                DWORD okEffects = DROPEFFECT_NONE;
                CHECK_FAILURE(args->get_AllowedDropEffects(&okEffects));
                CHECK_FAILURE(args->get_Data(&dragData));

                // This member refers to an implementation of IDropSource. It is an
                // OLE interface that is necessary to initiate drag in an application.
                // https://learn.microsoft.com/en-us/windows/win32/api/oleidl/nn-oleidl-idropsource
                if (!m_dropSource)
                {
                    m_dropSource = Make<ScenarioDragDropOverrideDropSource>();
                }

                DWORD effect = DROPEFFECT_NONE;
                HRESULT hr = DoDragDrop(dragData.get(), m_dropSource.get(), okEffects, &effect);
                args->put_Handled(TRUE);

                return hr;
            })
            .Get(),
        &m_dragStartingToken));
```

#### remove_DragStarting

Removes an event handler previously added with `add_DragStarting`.

> public HRESULT [remove_DragStarting](#remove_dragstarting)(EventRegistrationToken token)

