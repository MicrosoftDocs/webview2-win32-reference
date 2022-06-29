---
description: A Receiver is created for a particular DevTools Protocol event and allows you to subscribe and unsubscribe from that event.
title: WebView2 Win32 C++ ICoreWebView2DevToolsProtocolEventReceiver
ms.date: 06/29/2022
keywords: IWebView2, IWebView2WebView, webview2, webview, win32 apps, win32, edge, ICoreWebView2, ICoreWebView2Controller, browser control, edge html, ICoreWebView2DevToolsProtocolEventReceiver
---

# interface ICoreWebView2DevToolsProtocolEventReceiver

```
interface ICoreWebView2DevToolsProtocolEventReceiver
  : public IUnknown
```

A Receiver is created for a particular DevTools Protocol event and allows you to subscribe and unsubscribe from that event.

## Summary

 Members                        | Descriptions
--------------------------------|---------------------------------------------
[add_DevToolsProtocolEventReceived](#add_devtoolsprotocoleventreceived) | Subscribe to a `DevToolsProtocol` event.
[remove_DevToolsProtocolEventReceived](#remove_devtoolsprotocoleventreceived) | Remove an event handler previously added with `add_DevToolsProtocolEventReceived`.

Obtained from the WebView object using `GetDevToolsProtocolEventReceiver`.

## Applies to

Product                         | Introduced
--------------------------------|---------------------------------------------
WebView2 Win32            |    0.9.430
WebView2 Win32 Prerelease |    0.9.488

## Members

#### add_DevToolsProtocolEventReceived

Subscribe to a `DevToolsProtocol` event.

> public HRESULT [add_DevToolsProtocolEventReceived](#add_devtoolsprotocoleventreceived)([ICoreWebView2DevToolsProtocolEventReceivedEventHandler](icorewebview2devtoolsprotocoleventreceivedeventhandler.md) * handler, EventRegistrationToken * token)

The `Invoke` method of the `handler` runs whenever the corresponding `DevToolsProtocol` event runs. `Invoke` runs with an event args object containing the parameter object of the DevTools Protocol event as a JSON string.

```cpp
// Prompt the user to name a CDP event, and then subscribe to that event.
void ScriptComponent::SubscribeToCdpEvent()
{
    TextInputDialog dialog(
        m_appWindow->GetMainWindow(),
        L"Subscribe to CDP Event",
        L"CDP event name:",
        L"Enter the name of the CDP event to subscribe to.\r\n"
            L"You may also have to call the \"enable\" method of the\r\n"
            L"event's domain to receive events (for example \"Log.enable\").\r\n",
        L"Log.entryAdded");
    if (dialog.confirmed)
    {
        std::wstring eventName = dialog.input;
        wil::com_ptr<ICoreWebView2DevToolsProtocolEventReceiver> receiver;
        CHECK_FAILURE(
            m_webView->GetDevToolsProtocolEventReceiver(eventName.c_str(), &receiver));

        // If we are already subscribed to this event, unsubscribe first.
        auto preexistingToken = m_devToolsProtocolEventReceivedTokenMap.find(eventName);
        if (preexistingToken != m_devToolsProtocolEventReceivedTokenMap.end())
        {
            CHECK_FAILURE(receiver->remove_DevToolsProtocolEventReceived(
                preexistingToken->second));
        }

        CHECK_FAILURE(receiver->add_DevToolsProtocolEventReceived(
            Callback<ICoreWebView2DevToolsProtocolEventReceivedEventHandler>(
                [this, eventName](
                    ICoreWebView2* sender,
                    ICoreWebView2DevToolsProtocolEventReceivedEventArgs* args) -> HRESULT 
                {
                    wil::unique_cotaskmem_string parameterObjectAsJson;
                    CHECK_FAILURE(args->get_ParameterObjectAsJson(&parameterObjectAsJson));
                    std::wstring title = eventName;
                    std::wstring details = parameterObjectAsJson.get();
                    wil::com_ptr<ICoreWebView2DevToolsProtocolEventReceivedEventArgs2> args2;
                    if (SUCCEEDED(args->QueryInterface(IID_PPV_ARGS(&args2))))
                    {
                        wil::unique_cotaskmem_string sessionId;
                        CHECK_FAILURE(args2->get_SessionId(&sessionId));
                        if (sessionId.get() && *sessionId.get())
                        {
                            title = eventName + L" (session:" + sessionId.get() + L")";
                            std::wstring targetId = m_devToolsSessionMap[sessionId.get()];
                            std::wstring targetLabel = m_devToolsTargetLabelMap[targetId];
                            details = L"From " + targetLabel + L" (session:" + sessionId.get() +
                                      L")\r\n" + details;
                        }
                    }
                    m_appWindow->AsyncMessageBox(details, L"CDP Event Fired: " + title);
                    return S_OK;
                })
                .Get(),
            &m_devToolsProtocolEventReceivedTokenMap[eventName]));
    }
}
```

#### remove_DevToolsProtocolEventReceived

Remove an event handler previously added with `add_DevToolsProtocolEventReceived`.

> public HRESULT [remove_DevToolsProtocolEventReceived](#remove_devtoolsprotocoleventreceived)(EventRegistrationToken token)

